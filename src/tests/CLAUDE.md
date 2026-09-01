# src/tests/ — Catch2 unit tests

A deliberately small suite. OpenTTD's real safety net is the [regression tests](../../regression/CLAUDE.md) and the fact that people play the nightlies; this directory covers the pure, side-effect-free pieces where a unit test actually pays off — bit math, string handling, UTF-8, containers, tile-area geometry, the network crypto handshake.

Framework: **Catch2 v2.13.10**, vendored at [../3rdparty/catch2/catch.hpp](../3rdparty/catch2/catch.hpp). Note that this is the v2 single-header API (`#include "catch.hpp"`, `TEST_CASE`, `CHECK`, `REQUIRE`), not Catch2 v3 — v3 examples found online will not compile.

## Running

```powershell
cmake --build build --target openttd_test
ctest --test-dir build
```

Tests link against `openttd_lib`, so the whole game is available, and `catch_discover_tests` registers each `TEST_CASE` with CTest individually.

## Writing one

```cpp
/** @file math_func.cpp Test functionality from core/math_func. */

#include "../stdafx.h"

#include "../3rdparty/catch2/catch.hpp"

#include "../core/math_func.hpp"

#include "../safeguards.h"

TEST_CASE("DivideApproxTest - Negative")
{
	CHECK(-2 == DivideApprox(-5, 2));
}
```

The include order matters as much as it does anywhere else in [src/](../CLAUDE.md): `stdafx.h` first, `catch.hpp` next, then the header under test, and `safeguards.h` last. Paths are relative (`../core/...`) — this directory is not on the include path as a root.

Then register the file in [CMakeLists.txt](CMakeLists.txt) with **`add_test_files`**, not `add_files` — that variant targets `openttd_test` instead of the game binary. An unregistered file compiles nowhere and fails silently.

## Mocks

`mock_environment.h`, `mock_fontcache.h` and `mock_spritecache.h/.cpp` stand in for subsystems that would otherwise need a running game — enough to test code that touches sprites, fonts or window descriptions without initialising graphics. `test_window_desc.cpp` uses them to validate every `WindowDesc` in the game at test time, which is why a malformed widget tree fails here rather than at runtime.
