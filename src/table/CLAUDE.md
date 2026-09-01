# src/table/ — static data tables

Headers full of `static const` data, included exactly once by the `.cpp` that owns them. They are conventionally included last in the include block, just before `safeguards.h`, and they intentionally define data at namespace scope in a header — that is the pattern here, not a mistake.

Examples: `engines.h` (every vehicle in the game), `build_industry.h`, `airport_defaults.h`, `railtypes.h` / `roadtypes.h`, `pricebase.h`, `townname.h` (3200 lines of name fragments), `sprites.h` (the sprite ID enum), `palettes.h`, `control_codes.h`.

Editing one of these changes game balance or game state, so a change usually needs a savegame version bump — see [../saveload/CLAUDE.md](../saveload/CLAUDE.md).

## settings/ — the one part that is generated

[settings/](settings/) holds ~20 `.ini` files that `settingsgen` (built from [../settingsgen/](../settingsgen/)) compiles into `<build>/generated/table/settings.h`. **This is where you add or change a game setting** — never the generated header, and never the `openttd.cfg` parser.

Each `.ini` has four kinds of section:

- `[pre-amble]` — raw C++ emitted before the table: callback declarations and the `std::initializer_list<std::string_view>` value-name lists used by `SDTC_OMANY` settings, plus the opening `static const SettingVariant _gui_settings_table[] = {`.
- `[post-amble]` — the closing `};`.
- `[templates]` — the macro shapes (`SDTC_BOOL`, `SDTC_VAR`, `SDTC_OMANY`, `SDT_*` …) with `$var`, `$def`, `$min`, `$max`, `$from`, `$to` placeholders.
- `[validation]` — `static_assert`s applied to every generated row, e.g. checking that `$max` fits the declared storage type.
- Then one `[SDTC_…]` / `[SDT_…]` block per setting, filling in those placeholders.

`settings.h.preamble` and `settings.h.postamble` in this directory wrap the whole concatenated result — the preamble carries the shared includes, callback declarations and helper functions every settings table needs; the postamble is currently empty but is still passed to `settingsgen` via `-a`.

Things that bite:

- `$from` / `$to` are **savegame versions**. A setting saved in the game state needs its `from` set to the `SaveLoadVersion` entry you add, or old savegames get garbage.
- `SDT_*` settings live in the game state (saved in the savegame, shared by all clients); `SDTC_*` settings are client-local (`openttd.cfg` only). Choosing the wrong one either desyncs multiplayer or makes a preference unexpectedly global. See the state discussion in [../CLAUDE.md](../CLAUDE.md).
- `$str`, `$strhelp` and `$strval` are `STR_…` identifiers that must exist in [../lang/english.txt](../lang/CLAUDE.md), or the build fails on the generated header.
- The `.ini` files use `;` for comments, not `#`.
- New `.ini` files must be added to `TABLE_INI_SOURCE_FILES` in [settings/CMakeLists.txt](settings/CMakeLists.txt); order in that list is the order in the generated file.
