# CLAUDE.md

Guidance for Claude Code (claude.ai/code) working in this repository.

## What this repository is

A **personal fork of OpenTTD** — the open source reimplementation of *Transport Tycoon Deluxe*. It is a large C++20 codebase (~1400 files, ~410k LOC) built with CMake.

- `origin` → `https://github.com/animagr/OpenTTD.git` (this fork)
- `upstream` → `https://github.com/OpenTTD/OpenTTD.git` (the official project)
- Working branch: `master`, tracking upstream `master`.

On top of the upstream tree, this fork carries **local, untracked additions** for actually playing the game:

| Path | What it is | Tracked? |
| --- | --- | --- |
| [opengfx-8.0/](opengfx-8.0/) | Extracted OpenGFX 8.0 base graphics set (the free replacement for the original TTD graphics) | no |
| `opengfx-8.0.tar` | The same set as a tar, the form OpenTTD reads directly from `baseset/` | no |
| [OpenTTD Guide.md](OpenTTD%20Guide.md) | A ~970-line beginner-to-intermediate play guide, written from the official wiki manual | no |
| [OpenTTD Codebase Overview.html](OpenTTD%20Codebase%20Overview.html) | A self-contained illustrated tour of the codebase for a newcomer — game loop, tile map, commands, how the AI runs. Also published as an artifact | no |

These are **assets and notes, not source** — the graphics to run the game, a guide to playing it, and a guide to reading it. Leaving them untracked is deliberate — see the fork policy below — and it is why `git status` shows untracked files on an otherwise clean checkout.

## Fork policy: pull from upstream, never push to it

This fork **consumes** upstream and contributes nothing back. No pull requests, no issues, no patches. Assume that is settled and do not offer to upstream a change.

**LLM-authored code is fine here.** [CONTRIBUTING.md](CONTRIBUTING.md) carries a no-LLM policy under "Use of AI", but that is upstream's rule for submissions to *their* repository. It does not constrain work in this fork, and it is noted here only so it is not rediscovered and mistaken for a blocker each session.

What *does* matter is that upstream is pulled in regularly, so the tree has to stay mergeable:

```powershell
git fetch upstream
git rebase upstream/master     # or merge, if local history is worth preserving
```

Practical consequences for how changes should be made:

- **Every upstream file you edit is a permanent future conflict.** Prefer adding a new file over modifying an existing one, and keep unavoidable edits small and localised.
- **Never bulk-reformat, re-wrap or gratuitously modernise upstream code.** Churn that gains nothing costs conflicts on every pull, forever.
- **Keep local additions untracked or on their own branch.** Files git does not track cannot conflict — which is why the OpenGFX set, the guide and these `CLAUDE.md` files are left untracked.
- **Follow upstream's style and commit grammar anyway.** Not for review — nobody reviews this — but because consistent code rebases cleanly and keeps `git blame` legible against upstream history.
- Upstream's CI never runs here, so its checks are informational: they tell you what upstream considers broken in code you will keep merging with.

## Code map

A [.codemapy/](.codemapy/) scan is present. Read [.codemapy/summary.md](.codemapy/summary.md) before answering structural or feasibility questions — it has the directory/LOC breakdown, entry points, dependency hubs and cycles. `context.json` and `symbols.json` hold the full per-file symbol and import data.

The biggest fan-in headers are `src/stdafx.h` (556), `src/safeguards.h` (554) and `src/debug.h` (170) — touching them recompiles essentially everything.

## Building (Windows / MSVC, this machine's setup)

Dependencies come from **vcpkg**, static triplet. Ports needed: `breakpad`, `liblzma`, `libpng`, `lzo`, `zlib`.

```powershell
cmake -B build -G "Visual Studio 17 2022" `
      -DCMAKE_TOOLCHAIN_FILE="<vcpkg>\scripts\buildsystems\vcpkg.cmake" `
      -DVCPKG_TARGET_TRIPLET="x64-windows-static"
cmake --build build --config RelWithDebInfo
```

`build*` is gitignored, so any build directory whose name starts with `build` is safe. With no `CMAKE_BUILD_TYPE` you get a **Debug** build with asserts — far slower, but it catches problems early. Minimum CMake is 3.16; the compiler must support C++20.

Useful options (full list in [COMPILING.md](COMPILING.md)):

- `-DCMAKE_BUILD_TYPE=RelWithDebInfo` — release speed, still debuggable.
- `-DOPTION_DEDICATED=ON` — headless server, no GUI, fewer libraries.
- `-DOPTION_TOOLS_ONLY=ON` — build only `strgen` / `settingsgen`.
- `-DOPTION_USE_ASSERTS=OFF` — use with care.

## Testing

Two independent suites:

```powershell
# Catch2 unit tests -> target openttd_test, auto-registered with CTest
cmake --build build --target openttd_test
ctest --test-dir build

# AI/GameScript regression -> runs the game headless, diffs output against result.txt
cmake --build build --target regression
```

The `regression` target is preferred over invoking it through CTest — it is more verbose and resolves dependencies correctly. See [regression/CLAUDE.md](regression/CLAUDE.md).

## Generated code — never hand-edit these

Three generators run at build time and write into `<build>/generated/`, which is on the include path as `table/…`:

| Generated file | Produced by | From |
| --- | --- | --- |
| `table/strings.h` | `strgen` | [src/lang/english.txt](src/lang/english.txt) |
| `table/settings.h` | `settingsgen` | [src/table/settings/](src/table/settings/)`*.ini` plus `settings.h.preamble` / `.postamble` |
| `script/api/{ai,game}/*.sq.hpp` | CMake + `squirrel_export.sq.hpp.in` | [src/script/api/](src/script/api/)`script_*.hpp` |

If a `STR_…` symbol or a setting cannot be found, the fix is almost always in the *source* file above, not in the generated header.

## Coding style essentials

Full rules in [CODINGSTYLE.md](CODINGSTYLE.md); [.editorconfig](.editorconfig) encodes much of it. The ones that actually get changes rejected:

- **Tabs for indentation**, only at the start of a line. No trailing whitespace anywhere — CI enforces this.
- Every `.cpp` includes **`stdafx.h` first** and **`safeguards.h` last**, after everything else including `table/*.h`. `safeguards.h` `#define`s `malloc`, `strdup`, `sprintf` and friends to a poison macro, so anything included after it breaks.
- Every file needs a Doxygen `/** @file … */` block, or **nothing in that file gets documented at all**.
- `/* */` for standalone comments, `//` only at the end of a code line, `///<` for member and variable docs.
- Do not `typedef` enums or structs. Do not put `extern` declarations in `.cpp` files.
- Explicit comparisons: `if (p != nullptr && *p != '\0')`, not `if (p && *p)`.
- ASCII only in C++ sources, comments included.
- Line length is unlimited; when splitting, indent the continuation two extra tabs.

### When the global C++ rules conflict

`C:\Claude\CppRules.md` applies here, using the escape hatch it states itself: **style yields to the codebase, safety does not.** Concretely, in this repository:

| Yields to OpenTTD | Still applies |
| --- | --- |
| `m_`/`s_`/`k` prefixes → no prefix, but `this->` is mandatory for members | `enum class` (379 scoped vs 215 unscoped already) |
| camelCase locals → `lowercase_underscores` | No floats for money — `Money` is `OverflowSafeInt64` |
| PascalCase filenames → `lowercase_underscores.cpp` | RAII and no raw allocation — `safeguards.h` enforces it mechanically |
| `#pragma once` → classic `#ifndef` guards (556 files use them, one does not) | Everything in the security, error-handling and input-validation sections |
| "avoid mutable globals" → ~200 `_`-prefixed globals are the architecture | `[[nodiscard]]` where a return must not be dropped |
| Include order → `stdafx.h` first, `safeguards.h` last | Anything CppRules covers that CODINGSTYLE.md is silent on: concurrency, testing, logging, build config |

PascalCase functions and classes are the same in both, so the most visible convention transfers unchanged.

One inversion worth knowing: both documents ban `rand()`, for opposite reasons. CppRules wants unpredictability; OpenTTD wants *reproducibility*, because game state must replay identically on every client. Use the seeded `RandomRange()` for anything touching game state, and a CSPRNG only for secrets in [src/network/](src/network/CLAUDE.md). Applying either rule on the other's code path is a bug.

## Commit messages

A check-script on the git server enforces the format; malformed messages fail CI. Grammar:

```
<keyword>( #<issue>|<commit>)?: ([<component>])? <details>
```

Player-facing keywords: `Feature`, `Add`, `Change`, `Fix`, `Remove`, `Revert`, `Doc`, `Update`.
Developer-facing: `Codechange`, `Cleanup`, `Codefix`.
`[NewGRF]` and `[Script]` components mark author-facing changes; other components include `[Network]`, `[YAPF]`, `[CI]`, `[CMake]`, `[Windows]`.

`<details>` starts with a capital and does **not** end with a dot. Describe what the *player* notices, not what the code does. Use exactly one keyword. Examples:

```
Fix #5926: [YAPF] Infinite loop in pathfinder
Codefix 80dffae: Warning about unsigned unary minus
Codechange: Rewrite the autoreplace kernel
```

Commit or push only when asked. This is a fork, so local experiments do not need upstream-grade messages, but matching the grammar keeps rebases onto upstream clean.

## Repository layout

Directories with their own `CLAUDE.md` carry rules that will bite if missed — read them before editing there.

| Path | Contents |
| --- | --- |
| [src/](src/) | All game code — see [src/CLAUDE.md](src/CLAUDE.md) |
| [src/saveload/](src/saveload/) | Savegame reading/writing and version migration — [CLAUDE.md](src/saveload/CLAUDE.md) |
| [src/script/](src/script/) | Squirrel VM and the AI/GameScript API — [CLAUDE.md](src/script/CLAUDE.md) |
| [src/lang/](src/lang/) | Translations; `english.txt` is the master — [CLAUDE.md](src/lang/CLAUDE.md) |
| [src/network/](src/network/) | Client/server, coordinator, content service — [CLAUDE.md](src/network/CLAUDE.md) |
| [src/table/](src/table/) | Static data tables and the settings `.ini` sources — [CLAUDE.md](src/table/CLAUDE.md) |
| [src/tests/](src/tests/) | Catch2 unit tests — [CLAUDE.md](src/tests/CLAUDE.md) |
| [src/3rdparty/](src/3rdparty/) | Vendored libraries; do not edit — [CLAUDE.md](src/3rdparty/CLAUDE.md) |
| [bin/](bin/) | Runtime data dir: script compatibility layers, example console scripts — [CLAUDE.md](bin/CLAUDE.md) |
| [media/](media/) | Icons, fonts and the built-in base sets — [CLAUDE.md](media/CLAUDE.md) |
| [regression/](regression/) | AI/GS regression tests — [CLAUDE.md](regression/CLAUDE.md) |
| [cmake/](cmake/) | Build-system modules and `Find*` scripts — [CLAUDE.md](cmake/CLAUDE.md) |
| [.github/](.github/) | CI workflows and lint scripts — [CLAUDE.md](.github/CLAUDE.md) |
| [opengfx-8.0/](opengfx-8.0/) | Local graphics base set, not upstream — [CLAUDE.md](opengfx-8.0/CLAUDE.md) |
| [docs/](docs/) | Format and subsystem documentation: savegame format, desync debugging, linkgraph, admin network, landscape grid, fonts |
| [os/](os/) | Per-platform packaging: NSIS and Windows Store, macOS bundle and notarisation, emscripten, Steam/GOG manifests |

## Playing the build

[OpenTTD Guide.md](OpenTTD%20Guide.md) is the user's own reference, organised as:

- **Quick Reference** — the core loop, money facts, hotkeys, and the three rules that prevent most beginner disasters.
- **Part 1** — a 30-minute tutorial (bus route → train route → plane route), then world generation for a first real map.
- **Parts 2–9** — reference sections: growing a railway and signals, railway construction in detail, roads, airports, water transport, terrain/bridges/tunnels, orders and fleet management, and options/AI opponents/sandbox tools.

If the user asks a gameplay question, answer from this guide before reaching for the wiki — it is what they are following.

A build needs a **graphics base set** before it will start; that is what `opengfx-8.0` is for. Install it by copying `opengfx-8.0.tar` (or the extracted folder) into the `baseset/` subdirectory of an OpenTTD data directory — on Windows, `C:\Users\<username>\Documents\OpenTTD\baseset\`. OpenTTD reads uncompressed tars directly. [docs/directory_structure.md](docs/directory_structure.md) documents the full search order and where saves, screenshots, NewGRFs, AIs and scripts each belong.
