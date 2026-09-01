# regression/ — AI and GameScript regression tests

The real test suite for [../src/script/](../src/script/CLAUDE.md). Each test is a Squirrel script that drives the scripting API against a fixed savegame and prints as it goes; the run is compared byte for byte against a recorded `result.txt`. Determinism is the whole point — as the test's own description puts it, "on the same map the result should always be the same."

Four suites, each a subdirectory with the same shape (`info.nut`, `main.nut`, `test.sav`, `result.txt`):

| Suite | Covers |
| --- | --- |
| [regression/](regression/) | The bulk of the AI API — lists, settings, commands, events, pathfinding |
| [stationlist/](stationlist/) | `AIStationList` and friends |
| [gs/](gs/) | GameScript API |
| [gs_compat/](gs_compat/) | GameScript compatibility layers from [../bin/game/](../bin/CLAUDE.md) |

## Running

```powershell
cmake --build build --target regression          # all suites
cmake --build build --target regression_gs       # one suite
```

They are also registered with CTest (`RUN_SERIAL`, since they share a working directory), but the custom target is preferred — it is more verbose and resolves dependencies correctly.

Under the hood ([../cmake/scripts/Regression.cmake](../cmake/scripts/Regression.cmake)) each suite copies its files into the build tree and runs the game headless:

```
openttd -x -c regression/regression.cfg -g <suite>/test.sav -snull -mnull -vnull:ticks=30000 -d script=2 -Q
```

Null sound, music and video drivers; 30000 ticks; script debug level 2; `-Q` to quit when done. On Windows the binary is first copied and `editbin /subsystem:console` applied, because the GUI subsystem swallows stdout. **Anything on stdout, or any `crash*.log`, fails the test outright** — the expected output all goes to stderr.

## When a test fails

The diff against `result.txt` is the failure. Two very different causes:

- **A regression.** Something you changed altered API behaviour. Fix the code.
- **An intended change.** You deliberately changed what the API returns or prints, so the recorded output is now stale. Update `result.txt` — but read the diff line by line first, because it is equally capable of hiding an unintended change three lines further down.

Never regenerate `result.txt` wholesale without reading it. It is the only record of what the API used to do.

## Adding coverage

Extend the relevant `main.nut` and re-record. Note that `info.nut` pins `GetAPIVersion()` (currently `"16"`) — the suites deliberately test against a specific API version, and `gs_compat` exists precisely to exercise the older ones.

[regression.cfg](regression.cfg) fixes every setting the tests depend on (`plane_speed = 2`, `autosave = off`, `max_bridge_length = 100`, English town names, …). If a test's output shifts for no obvious reason, check whether a default you changed is one this config does *not* pin — that is a sign the setting should be added here.
