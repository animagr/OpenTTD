# bin/ — runtime data shipped alongside the binary

Not build output. This is source-controlled *game data* that gets copied next to the executable and installed with it. Three things live here.

## ai/ and game/ — script compatibility layers

`compat_<version>.nut` for every API version OpenTTD still supports: `0.7` through `15` for AIs, `1.2` through `15` for GameScripts. Each file is Squirrel that runs before an old script starts and **downgrades the current API to look like that version** — `compat_15.nut` opens with "This file contains code to downgrade the API from 16 to 15."

This is the mechanism that keeps published AIs and GameScripts working across releases. When you rename or remove something in [../src/script/api/](../src/script/api/), the old name has to be reimplemented here for every version that had it, or every script targeting those versions breaks. See [../src/script/CLAUDE.md](../src/script/CLAUDE.md).

A new compat file also needs adding to `AI_COMPAT_SOURCE_FILES` / the matching list in [ai/CMakeLists.txt](ai/CMakeLists.txt) or [game/CMakeLists.txt](game/CMakeLists.txt), and the new version needs adding to `AIInfo::ApiVersions` / `GameInfo::ApiVersions`.

Existing compat files are effectively frozen — editing one changes behaviour for already-published scripts that have no way to adapt.

## scripts/ — console script examples

`autoexec.scr.example` and `game_start.scr.example`. Both are *examples*: OpenTTD looks for `autoexec.scr` and `game_start.scr` (no `.example`) in the user's data directory, so these are templates to copy, and editing them affects nobody's game.

- `autoexec.scr` runs at startup — console aliases and settings. The shipped example defines `alias s "say %!"` so `] s hello` sends a chat message.
- `game_start.scr` runs when a game starts — the example is a single `start_ai MyAI`.

## What is *not* here

The `baseset/`, `lang/`, `ai/`, `game/` and `scenario/` directories that appear next to an installed binary are assembled at build/install time from [../media/](../media/CLAUDE.md) and [../src/lang/](../src/lang/CLAUDE.md). Don't add graphics or `.lng` files to this directory.

Where those files end up at runtime, and the search order OpenTTD uses to find them, is documented in [../docs/directory_structure.md](../docs/directory_structure.md). The local OpenGFX copy in [../opengfx-8.0/](../opengfx-8.0/CLAUDE.md) is installed into the user's data directory, not here.
