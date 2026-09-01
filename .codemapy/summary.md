# codemapy summary

- Root: `C:\Claude\Testing\OpenTTD`
- Generated: `2026-08-31T19:11:09.843968+00:00`
- Git commit: `96651d379a94` (dirty working tree)
- Files: 1383
- LOC: 411139
- Internal dependencies: 8818
- External references: 1172
- Symbols: 18465
- Dependency cycles: 1

## Languages

- C Header: 633 files
- C++: 561 files
- C++ Header: 180 files
- Python: 6 files
- Shell: 2 files
- JavaScript: 1 file

## Directory Overview

- `src/`: 1375 files, 410527 loc (C Header)
- `.github/`: 5 files, 338 loc (Python)
- `os/`: 3 files, 274 loc (JavaScript)

## Entry Points

- `src/settingsgen/settingsgen.cpp` (defines main())
- `src/strgen/strgen.cpp` (defines main())
- `src/os/macosx/osx_main.cpp` (defines main())
- `src/os/unix/unix_main.cpp` (defines main())
- `.github/changelog.py` (__main__ guard)
- `.github/file-descriptions.py` (__main__ guard)
- `.github/script-missing-mode-enforcement.py` (__main__ guard)

## Top Hubs

- `src/stdafx.h`: fan-in 556, fan-out 1, 258 loc
- `src/safeguards.h`: fan-in 554, fan-out 0, 100 loc
- `src/debug.h`: fan-in 170, fan-out 2, 121 loc
- `src/string_func.h`: fan-in 161, fan-out 1, 126 loc
- `src/strings_func.h`: fan-in 160, fan-out 3, 181 loc
- `src/window_func.h`: fan-in 109, fan-out 4, 68 loc
- `src/company_func.h`: fan-in 106, fan-out 4, 54 loc
- `src/timer/timer_game_calendar.h`: fan-in 105, fan-out 1, 44 loc
- `src/company_base.h`: fan-in 94, fan-out 7, 162 loc
- `src/command_func.h`: fan-in 89, fan-out 7, 471 loc

## Largest Files

- `src/3rdparty/nlohmann/json.hpp`: 21595 loc
- `src/3rdparty/catch2/catch.hpp`: 14825 loc
- `src/3rdparty/opengl/glext.h`: 12267 loc
- `src/station_cmd.cpp`: 4638 loc
- `src/3rdparty/fmt/format.h`: 3802 loc
- `src/train_cmd.cpp`: 3622 loc
- `src/town_cmd.cpp`: 3586 loc
- `src/viewport.cpp`: 3305 loc
- `src/table/townname.h`: 3196 loc
- `src/vehicle_gui.cpp`: 3160 loc

## Dependency Cycles

- 3 files: `src/3rdparty/fmt/base.h` <-> `src/3rdparty/fmt/format-inl.h` <-> `src/3rdparty/fmt/format.h`

## Symbols by Kind

- function: 14829
- struct: 1648
- enum: 778
- class: 678
- namespace: 292
- type: 240

## External References

- `table/strings.h`: 197
- `string`: 55
- `vector`: 45
- `utility`: 37
- `algorithm`: 34
- `memory`: 29
- `type_traits`: 27
- `cstddef`: 26
- `iterator`: 23
- `windows.h`: 23
- `cassert`: 17
- `chrono`: 17
- `cstdint`: 17
- `mutex`: 17
- `cmath`: 16
- `cstring`: 15
- `limits`: 14
- `unistd.h`: 14
- `array`: 12
- `cstdio`: 12

## Documentation Files

- `CODINGSTYLE.md` (458 loc)
- `COMPILING.md` (116 loc)
- `CONTRIBUTING.md` (188 loc)
- `COPYING.md` (282 loc)
- `CREDITS.md` (57 loc)
- `OpenTTD Guide.md` (966 loc)
- `README.md` (131 loc)
- `changelog.md` (7223 loc)
- `known-bugs.md` (328 loc)
- `.github/PULL_REQUEST_TEMPLATE.md` (45 loc)
- `docs/admin_network.md` (180 loc)
- `docs/compiling_lang_files.md` (48 loc)
- `docs/debugging_desyncs.md` (49 loc)
- `docs/desync.md` (216 loc)
- `docs/directory_structure.md` (115 loc)
- ... and 96 more

## Project Metadata Files

- `CMakeLists.txt`: project-metadata, 393 loc, 16374 bytes
- `bin/CMakeLists.txt`: project-metadata, 2 loc, 46 bytes
- `bin/ai/CMakeLists.txt`: project-metadata, 38 loc, 1650 bytes
- `bin/game/CMakeLists.txt`: project-metadata, 35 loc, 1515 bytes
- `media/CMakeLists.txt`: project-metadata, 81 loc, 3652 bytes
- `media/baseset/CMakeLists.txt`: project-metadata, 80 loc, 3956 bytes
- `media/baseset/openttd/CMakeLists.txt`: project-metadata, 65 loc, 4335 bytes
- `media/baseset/orig_extra/CMakeLists.txt`: project-metadata, 40 loc, 2642 bytes
- `regression/CMakeLists.txt`: project-metadata, 23 loc, 1198 bytes
- `regression/gs/CMakeLists.txt`: project-metadata, 8 loc, 271 bytes
- `regression/gs_compat/CMakeLists.txt`: project-metadata, 7 loc, 226 bytes
- `regression/regression/CMakeLists.txt`: project-metadata, 8 loc, 269 bytes
- `regression/stationlist/CMakeLists.txt`: project-metadata, 7 loc, 224 bytes
- `src/3rdparty/CMakeLists.txt`: project-metadata, 9 loc, 257 bytes
- `src/3rdparty/catch2/CMakeLists.txt`: project-metadata, 3 loc, 30 bytes
- `src/3rdparty/fmt/CMakeLists.txt`: project-metadata, 18 loc, 228 bytes
- `src/3rdparty/icu/CMakeLists.txt`: project-metadata, 6 loc, 108 bytes
- `src/3rdparty/icu/tests/CMakeLists.txt`: project-metadata, 4 loc, 71 bytes
- `src/3rdparty/md5/CMakeLists.txt`: project-metadata, 4 loc, 39 bytes
- `src/3rdparty/monocypher/CMakeLists.txt`: project-metadata, 6 loc, 107 bytes
- `src/3rdparty/nlohmann/CMakeLists.txt`: project-metadata, 3 loc, 29 bytes
- `src/3rdparty/opengl/CMakeLists.txt`: project-metadata, 9 loc, 144 bytes
- `src/3rdparty/openttd_social_integration_api/CMakeLists.txt`: project-metadata, 4 loc, 94 bytes
- `src/3rdparty/squirrel/CMakeLists.txt`: project-metadata, 3 loc, 83 bytes
- `src/3rdparty/squirrel/include/CMakeLists.txt`: project-metadata, 5 loc, 64 bytes
- `src/3rdparty/squirrel/sqstdlib/CMakeLists.txt`: project-metadata, 4 loc, 52 bytes
- `src/3rdparty/squirrel/squirrel/CMakeLists.txt`: project-metadata, 29 loc, 467 bytes
- `src/CMakeLists.txt`: project-metadata, 598 loc, 11877 bytes
- `src/ai/CMakeLists.txt`: project-metadata, 14 loc, 230 bytes
- `src/blitter/CMakeLists.txt`: project-metadata, 44 loc, 890 bytes
- `src/core/CMakeLists.txt`: project-metadata, 36 loc, 745 bytes
- `src/fontcache/CMakeLists.txt`: project-metadata, 10 loc, 189 bytes
- `src/game/CMakeLists.txt`: project-metadata, 16 loc, 292 bytes
- `src/lang/CMakeLists.txt`: project-metadata, 128 loc, 5609 bytes
- `src/linkgraph/CMakeLists.txt`: project-metadata, 22 loc, 396 bytes
- `src/misc/CMakeLists.txt`: project-metadata, 15 loc, 285 bytes
- `src/music/CMakeLists.txt`: project-metadata, 44 loc, 791 bytes
- `src/network/CMakeLists.txt`: project-metadata, 40 loc, 885 bytes
- `src/network/core/CMakeLists.txt`: project-metadata, 48 loc, 804 bytes
- `src/newgrf/CMakeLists.txt`: project-metadata, 46 loc, 1134 bytes
- `src/os/CMakeLists.txt`: project-metadata, 3 loc, 77 bytes
- `src/os/macosx/CMakeLists.txt`: project-metadata, 16 loc, 320 bytes
- `src/os/unix/CMakeLists.txt`: project-metadata, 18 loc, 372 bytes
- `src/os/windows/CMakeLists.txt`: project-metadata, 15 loc, 324 bytes
- `src/pathfinder/CMakeLists.txt`: project-metadata, 8 loc, 153 bytes
- `src/pathfinder/yapf/CMakeLists.txt`: project-metadata, 24 loc, 483 bytes
- `src/saveload/CMakeLists.txt`: project-metadata, 50 loc, 979 bytes
- `src/saveload/compat/CMakeLists.txt`: project-metadata, 29 loc, 671 bytes
- `src/script/CMakeLists.txt`: project-metadata, 28 loc, 591 bytes
- `src/script/api/CMakeLists.txt`: project-metadata, 279 loc, 9851 bytes
- `src/settingsgen/CMakeLists.txt`: project-metadata, 20 loc, 671 bytes
- `src/sound/CMakeLists.txt`: project-metadata, 32 loc, 588 bytes
- `src/spriteloader/CMakeLists.txt`: project-metadata, 9 loc, 150 bytes
- `src/strgen/CMakeLists.txt`: project-metadata, 28 loc, 862 bytes
- `src/table/CMakeLists.txt`: project-metadata, 47 loc, 887 bytes
- `src/table/settings/CMakeLists.txt`: project-metadata, 56 loc, 2514 bytes
- `src/tests/CMakeLists.txt`: project-metadata, 23 loc, 525 bytes
- `src/timer/CMakeLists.txt`: project-metadata, 16 loc, 357 bytes
- `src/video/CMakeLists.txt`: project-metadata, 38 loc, 749 bytes
- `src/video/cocoa/CMakeLists.txt`: project-metadata, 13 loc, 210 bytes
- `src/widgets/CMakeLists.txt`: project-metadata, 63 loc, 1346 bytes

## Other Files

- `.grf`: 8 files, 6434290 bytes
- `.tar`: 1 file, 5396480 bytes
- `.png`: 62 files, 1146461 bytes
- `.nfo`: 35 files, 521185 bytes
- `.icns`: 1 file, 451284 bytes
- `.ttf`: 4 files, 310888 bytes
- `.sav`: 4 files, 223372 bytes
- `.bmp`: 3 files, 182468 bytes
- `.nut`: 41 files, 181967 bytes
- `.ini`: 20 files, 174816 bytes
- ... and 36 more extensions

## Artifact Guide

- `context.json`: full scan data - files, imports, dependency edges, cycles, per-file symbol counts
- `symbols.json`: per-file definitions plus an `index` mapping each defined name to its locations
- `hubs.json`: modules ranked by fan-in / fan-out
- `manifest.json`: generation metadata, artifact byte sizes, and `git_commit` for staleness checks
- `report.html`: visual file tree, treemap, dependency graph, and insights (entry points, hubs, cycles, per-file symbols) for humans
