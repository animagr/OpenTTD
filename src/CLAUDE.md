# src/ — OpenTTD game code

Everything the game is built from. ~1400 files, ~410k LOC of C++20. Read the root [CLAUDE.md](../CLAUDE.md) first for build commands, style rules and the fork policy — in particular, this is a pull-only fork, so every upstream file edited here becomes a future merge conflict.

## File naming — the suffix tells you what a file is

Most subsystems are spread across a family of files sharing a prefix. Knowing the suffix saves a search:

| Suffix | Contents |
| --- | --- |
| `*_type.h` | Enums, typedefs, small POD types. Cheap to include, no dependencies. |
| `*_base.h` | The main data structure(s) — usually a pool item, e.g. `Vehicle` in `vehicle_base.h`. |
| `*_func.h` | Free-function declarations operating on the subsystem. |
| `*_map.h` | Tile accessors — read/write the packed bits of a map tile, e.g. `IsRailDepot(tile)`. |
| `*_cmd.h` | Command *declarations* plus their `DEF_CMD_TRAIT` registrations. |
| `*_cmd.cpp` | Command *implementations* — the game-state-changing logic. |
| `*_gui.cpp` | Windows, widgets and everything the player clicks. Client-local. |
| `*_sl.cpp` | Savegame handling, but those live in [saveload/](saveload/CLAUDE.md). |

Layer discipline follows from this: `*_cmd.cpp` changes the game state, `*_gui.cpp` only asks it to. A GUI file should not mutate game state directly.

## Adding a source file

CMake does not glob. Every file is listed explicitly in the `add_files(...)` call of its directory's `CMakeLists.txt` (the function is defined in [../cmake/SourceList.cmake](../cmake/SourceList.cmake)). A new file that is not registered simply will not be compiled, with no error.

`add_files` accepts a `CONDITION` clause for optional dependencies:

```cmake
add_files(
    screenshot_png.cpp
    CONDITION PNG_FOUND
)
```

Test sources use `add_test_files` instead, which targets `openttd_test` — see [tests/CLAUDE.md](tests/CLAUDE.md).

## Include order is load-bearing

```cpp
#include "stdafx.h"      // always first
#include "command_func.h"
/* … the rest, roughly grouped … */
#include "table/strings.h"
#include "table/town_land.h"

#include "safeguards.h"  // always last, after a blank line
```

`safeguards.h` `#define`s `malloc`, `calloc`, `realloc`, `strdup`, `sprintf` and similar to `SAFEGUARD_DO_NOT_USE_THIS_METHOD`, so any header included after it will fail to compile if it names one of them. Its whole purpose is to stop unsafe C-string and allocation calls from creeping in — use `std::vector`, `std::unique_ptr`, `std::string` and `fmt`-style formatting instead.

## The command system

Anything that changes game state goes through a **command**. This is what makes multiplayer work: clients send commands, every client executes the same commands on the same frame, and the resulting state must match bit for bit.

Three pieces per command:

1. **Implementation** in `*_cmd.cpp` — `CommandCost CmdBuildSingleRail(DoCommandFlags flags, TileIndex tile, …)`.
2. **Declaration** in the matching `*_cmd.h`, plus a `DEF_CMD_TRAIT` line binding it to a `Commands::` enumerator:

   ```cpp
   DEF_CMD_TRAIT(Commands::BuildRail, CmdBuildSingleRail,
                 CommandFlags({CommandFlag::Auto, CommandFlag::NoWater}),
                 CommandType::LandscapeConstruction)
   ```

3. **Invocation**, typically from a GUI file:

   ```cpp
   Command<Commands::BuildRail>::Post(STR_ERROR_CAN_T_BUILD_RAILROAD_TRACK, CcPlaySound_CONSTRUCTION_RAIL, tile, …);
   ```

The `DoCommandFlags` parameter carries `DoCommandFlag::Execute` — a command is called first *without* it to compute cost and validity, then again *with* it to actually apply. **Both passes must reach the same verdict and the same cost**; if the test pass says yes and the execute pass fails, you get a desync. Return `CommandCost(STR_ERROR_…)` to refuse.

`Post` queues the command through the network layer; `Do` executes it directly (only valid where you are already inside command execution).

## Game state vs. client-local state

The single most common source of hard bugs. See [../docs/desync.md](../docs/desync.md).

- `_settings_game` — part of the game state, saved in the savegame, identical on every client. Safe to read in command code.
- `_settings_client` — this player's GUI preferences. **Never** let it influence game state; reading it in a `*_cmd.cpp` code path is a desync waiting to happen.
- `_settings_newgame` — the pending settings for the *next* game, only meaningful in the main menu.
- `_local_company` / `_current_company` — `_local_company` is who this client is playing as (client-local); `_current_company` is who the command is executing on behalf of (game state). Command code wants `_current_company`.

Anything non-deterministic — uninitialised memory, pointer values, iteration order of a hash container, floating-point, real time — must stay out of game state. Use `RandomRange()` from `core/random_func.hpp` (the seeded, savegame-persisted generator), never `rand()`.

## Pools

Vehicles, stations, towns, industries, orders and similar are stored in **pools** — sparse, index-addressed arrays with stable IDs that survive saving and loading.

```cpp
extern VehiclePool _vehicle_pool;
struct Vehicle : VehiclePool::PoolItem<&_vehicle_pool>, BaseVehicle, BaseConsist { … };
```

Pool item IDs are strong typedefs (`VehicleID`, `StationID`, …) with an `::Invalid()` sentinel, not raw integers. Iterate with the pool's iterators rather than a raw index loop, and remember that pool indices are holey: a valid index range does not mean every slot is occupied. Implementation lives in [core/pool_type.hpp](core/pool_type.hpp).

## GUI and widgets

A window is a `Window` subclass plus three declarations, usually all in the same `*_gui.cpp`:

- A widget-ID enum in [widgets/](widgets/)`<name>_widget.h` — `enum RailToolbarWidgets : WidgetID { WID_RAT_CAPTION, … }`. Every entry gets a `///<` comment; prefixes are short and must not collide across windows (hence `WID_RAT_` for rail toolbar, to avoid `WID_RT_` clashing with road).
- A `static constexpr std::initializer_list<NWidgetPart>` layout tree — nested `NWidget(...)` / `EndContainer()` calls describing the window's structure declaratively.
- A `static WindowDesc` tying the layout, the default position and size, the `.cfg` ini key, and the hotkey list together.

Strings never appear as literals: they are `StringID` constants generated from [lang/english.txt](lang/CLAUDE.md).

## Subdirectory map

| Path | Contents |
| --- | --- |
| [3rdparty/](3rdparty/CLAUDE.md) | Vendored libraries — fmt, nlohmann/json, squirrel, catch2, monocypher, ICU shims. Do not edit. |
| [ai/](ai/) | AI lifecycle: config, scanner, instance, GUI. The API itself is in `script/`. |
| [blitter/](blitter/) | Pixel blitters — 8bpp/32bpp, SSE2/SSSE3/SSE4 variants, selected at runtime via `factory.hpp`. |
| [core/](core/) | Foundational utilities: pools, bit math, strong typedefs, string builder/consumer, kd-tree, overflow-safe ints. |
| [fontcache/](fontcache/) | Platform font backends (FreeType, CoreText, Win32/Uniscribe). |
| [game/](game/) | GameScript lifecycle, mirroring `ai/`, plus `game_text.cpp` for GS-supplied strings. |
| [lang/](lang/CLAUDE.md) | Translations. `english.txt` is the only one to edit by hand. |
| [linkgraph/](linkgraph/) | Cargo distribution — demand, flow mapping, multi-commodity flow solver. |
| [misc/](misc/) | Assorted containers and helpers: binary heap, LRU cache, hash table, endian buffer, `getopt`. |
| [music/](music/), [sound/](sound/), [video/](video/) | Driver families. Each has a `*_driver.hpp` interface and platform implementations registered through a factory. |
| [network/](network/CLAUDE.md) | Client, server, game coordinator, STUN/TURN, content service, admin port, crypto. |
| [newgrf/](newgrf/) | NewGRF loading, split by action — `newgrf_act0_*.cpp` handles per-feature property definitions. |
| [os/](os/) | Per-OS entry points and platform glue (`unix_main.cpp`, `win32.cpp`, Cocoa). |
| [pathfinder/](pathfinder/) | YAPF (the production pathfinder) plus shared water-region and follow-track code. |
| [saveload/](saveload/CLAUDE.md) | Savegame format, chunk handlers, version migration, `afterload.cpp`. |
| [script/](script/CLAUDE.md) | Squirrel VM binding and the whole AI/GS API surface. |
| [settingsgen/](settingsgen/), [strgen/](strgen/) | Standalone build-time tools with their own `main()`. Built even under `OPTION_TOOLS_ONLY`. |
| [spriteloader/](spriteloader/) | Sprite decoding and the sprite cache. |
| [table/](table/CLAUDE.md) | Static data tables and the settings `.ini` sources. |
| [tests/](tests/CLAUDE.md) | Catch2 unit tests. |
| [timer/](timer/) | The four clocks — calendar, economy, tick, realtime — plus window timers. Calendar and economy dates diverge under wallclock timekeeping; pick the right one. |
| [widgets/](widgets/) | One widget-ID enum header per window. Headers only, no code. |
