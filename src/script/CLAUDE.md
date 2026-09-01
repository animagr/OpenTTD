# src/script/ — Squirrel VM and the AI / GameScript API

Two things live here: the embedding of the Squirrel language (`squirrel*.cpp/hpp`, plus the vendored VM in [../3rdparty/squirrel/](../3rdparty/squirrel/)), and the entire scripting **API surface** in [api/](api/) — 150-odd `script_*.hpp`/`.cpp` pairs that AIs and GameScripts call.

The lifecycle wrappers around this — scanning, configuring and instantiating scripts — are in [../ai/](../ai/) and [../game/](../game/), mirroring each other.

## This is a published, versioned API

Third-party AIs and GameScripts are distributed through OpenTTD's content service and must keep working across releases. That makes this directory the closest thing in the codebase to a public contract, and it is why several extra rules apply.

Supported API versions are listed in `AIInfo::ApiVersions` ([../ai/ai_info.hpp](../ai/ai_info.hpp)) and `GameInfo::ApiVersions` ([../game/game_info.hpp](../game/game_info.hpp)); a script declares which one it targets from `GetAPIVersion()` in its `info.nut`.

Changing the API means touching four places:

1. The `script_*.hpp` / `.cpp` pair in [api/](api/).
2. [api/ai_changelog.hpp](api/ai_changelog.hpp) and/or [api/game_changelog.hpp](api/game_changelog.hpp) — a Doxygen `\li` entry under the current unreleased version heading. These are the documents script authors actually read.
3. The compatibility layer, if a script written against an older API version would now break — see below.
4. `ApiVersions`, but only when opening a *new* API version, not for each change within one.

## Compatibility layers

[../../bin/ai/](../../bin/ai/) and [../../bin/game/](../../bin/game/) hold `compat_<version>.nut` files. Each one is Squirrel that runs before an old script starts and **downgrades the current API back to what that version looked like** — the header of `compat_15.nut` reads "This file contains code to downgrade the API from 16 to 15."

So when you rename or remove an API function, the old name does not vanish: it gets reimplemented in the compat layer for every version that had it. Removing a function without a compat entry breaks every published script that used it.

## Mode enforcement is CI-enforced

[../../.github/script-missing-mode-enforcement.py](../../.github/script-missing-mode-enforcement.py) runs on every PR. Its rule:

> A function that calls `ScriptObject::Command` or `ScriptObject::GetCompany` is "dangerous" and **must** also invoke one of the mode enforcement macros from `api/script_error.hpp` — `EnforceDeityMode`, `EnforceCompanyModeValid`, `EnforceCompanyModeValid_Void`, `EnforceDeityOrCompanyModeValid`, or `EnforceDeityOrCompanyModeValid_Void`.

Any dangerous function without one is a CI error. This exists because a GameScript runs as a deity with no company, while an AI runs as one — calling a company-scoped command from deity mode is otherwise a crash or a corrupted game state. Add the macro as the first statement of the function.

Related preconditions from the same header: `EnforcePrecondition(returnval, condition)`, `EnforcePreconditionCustomError`, `EnforcePreconditionEncodedText`.

## Generated bindings — do not look for `.sq` files in the tree

The Squirrel binding glue (`*.sq.hpp`) is **generated at build time** into `<build>/generated/script/api/{ai,game}/` from `squirrel_export.sq.hpp.in` by the rules in [api/CMakeLists.txt](api/CMakeLists.txt). It is not committed. Adding a new `script_*.hpp` means registering it in that `CMakeLists.txt`; the binding then appears on the next configure.

Hand-written exceptions are `{ai,game}/{ai,game}_controller.sq.hpp`, which do live in the tree.

## Documentation

The API docs published for script authors are built by Doxygen from `Doxyfile_AI.in` / `Doxyfile_GS.in`, fed through [api/doxygen_filter.sh](api/doxygen_filter.sh) and its awk script — that filter is what rewrites `Script*` class names into the `AI*` / `GS*` names authors see. Note the style exception from [../../CODINGSTYLE.md](../../CODINGSTYLE.md): NoAI `.hpp` files use `//!<` for single-line member comments, not `///<`.

## Scripts persist their own state

A script's memory is not reconstructed from the map on load — it is saved into the savegame. A script may implement `Save()`, returning a table, and `Load(version, data)` to read it back. `ScriptInstance::SaveObject` in [script_instance.cpp](script_instance.cpp) enforces the contract:

- Storable types are integer, string, array, table, bool and null. Nesting is capped at **25 levels** (`SQUIRREL_MAX_DEPTH`); exceeding it logs *"Savedata can only be nested to 25 deep. No data saved."*
- Class instances are rejected unless the underlying `ScriptObject` implements its own `SaveObject`; otherwise the script gets *"You tried to save an unsupported type. No data saved."*
- `Save()` runs on the main thread and **cannot issue commands** — only read-only API calls.
- It is called while the script is mid-execution, at whatever point the fair scheduler happens to be at, so a script that mutates the same structures it saves has a genuine race with itself.

On load, OpenTTD walks a fallback chain: the exact same script version, then the newest version whose `MinVersionToLoad()` accepts the saved data, then the newest version regardless, then a random script, and finally the built-in **dummy** script. That chain is why removing a published API can strand a savegame rather than merely a script.

Pending events are not saved. A script that cares about them has to serialise them itself.

## Testing and debugging a script

[../../regression/](../../regression/) is the real automated test of this directory — it drives the API from Squirrel and diffs against recorded output. See [../../regression/CLAUDE.md](../../regression/CLAUDE.md). There is also `test_script_admin.cpp` in [../tests/](../tests/).

For interactive work there is a set of console commands and a debug window:

| Tool | Use |
| --- | --- |
| `list_ai`, `start_ai <name>`, `stop_ai`, `reload_ai`, `rescan_ai` | Console commands to run one script without waiting for a company slot |
| `-d script=5` on the command line, or `debug_level script=5` in the console | Route script logging to stdout; the regression runner uses level 2 |
| AI/GS Debug window | Per-script log output, and a reload button that restarts a script from disk without restarting the game |
| `set gui.ai_developer_tools 1` | Unlocks break-on-log-message in the debug window and `ScriptController::Break()` |

`gui.ai_developer_tools` defaults to off and is an expert-category setting, which is why those controls are invisible until it is enabled.
