# cmake/ — build system modules

CMake 3.16 minimum. Three kinds of file live here: OpenTTD's own helper functions, `Find*` modules for dependencies CMake does not ship finders for, and packaging logic.

## The helpers you will actually use

**[SourceList.cmake](SourceList.cmake)** — `add_files()` and `add_test_files()`. Sources are never globbed; every file is listed by hand in its directory's `CMakeLists.txt`, so an unregistered file simply is not compiled and nothing warns you.

```cmake
add_files(
    screenshot_png.cpp
    CONDITION PNG_FOUND
)
```

`CONDITION` takes a complete `if()` expression, so `CONDITION SDL_FOUND AND Allegro_FOUND` works. `add_files` targets `openttd_lib`; `add_test_files` targets `openttd_test`. Both **hard-fail on duplicate basenames** across the whole target (some IDEs cannot cope with two `utils.cpp`), with headers under `3rdparty/` exempted — so a new file needs a name unique in the entire tree.

**[AddCustomXXXTimestamp.cmake](AddCustomXXXTimestamp.cmake)** — `add_custom_command_timestamp()` / `add_custom_target_timestamp()`, wrappers that add a timestamp file so generated outputs do not needlessly re-trigger downstream builds. Every generator in the tree (strgen, settingsgen, basesets) goes through these rather than plain `add_custom_command`.

**[Options.cmake](Options.cmake)** — where every `OPTION_*` is declared. Beyond the ones in [../COMPILING.md](../COMPILING.md): `OPTION_INSTALL_FHS`, `OPTION_PACKAGE_DEPENDENCIES`, `OPTION_USE_NSIS`, `OPTION_DOCS_ONLY` (which implies `OPTION_TOOLS_ONLY`), `OPTION_ALLOW_INVALID_SIGNATURE`, `OPTION_SURVEY_KEY`, and the Doxygen warning-file options.

**[SourceList.cmake](SourceList.cmake)'s sibling generators** in [scripts/](scripts/), each invoked via `cmake -P`:

| Script | Produces |
| --- | --- |
| `SquirrelExport.cmake`, `SquirrelIncludes.cmake` | The `*.sq.hpp` script bindings — [../src/script/](../src/script/CLAUDE.md) |
| `CreateGRF.cmake` | `openttd.grf` / `orig_extra.grf` via GRFCodec — [../media/](../media/CLAUDE.md) |
| `Baseset.cmake` | `.obg`/`.obm`/`.obs` metadata, with translated descriptions pulled from the lang files |
| `Regression.cmake` | Runs one regression suite — [../regression/](../regression/CLAUDE.md) |
| `GenerateWidget.cmake` | Fills the `// @enum … @endenum` placeholders in `script_window.hpp` by copying enums out of the real headers, so the script API's widget constants stay in sync with the game's |
| `FindVersion.cmake` | The version string baked into the binary, derived from git |
| `Desktop.cmake` | The freedesktop `.desktop` entry |

## Find modules

`FindAllegro`, `FindFluidsynth`, `FindFontconfig`, `FindHarfbuzz`, `FindIconv`, `FindLZO`, `FindOgg`, `FindOpus`, `FindOpusFile`, `FindSoxr`, `FindSSE`, `FindXaudio2`, `FindGrfcodec`, `FindEditbin`, `FindPandoc`. `FixVcpkgLibrary.cmake` and `Static.cmake` handle the static-triplet vcpkg builds this fork uses on Windows.

`FindGrfcodec` is the one with a side effect worth knowing about: finding GRFCodec makes the build regenerate committed `.grf` files into the *source* tree. See [../media/CLAUDE.md](../media/CLAUDE.md).

## Packaging

`InstallAndPackage.cmake` drives it, with per-format modules: `PackageNSIS` (Windows installer), `PackageBundle` (macOS `.app`), `PackageDeb`, `PackageRPM`, and `CPackProperties.cmake.in` at the repository root. `MSVCFilters.cmake` arranges the Visual Studio solution tree so the generated project mirrors the source layout.

## Changing anything here

A CMake change affects seven CI platforms — see [../.github/CLAUDE.md](../.github/CLAUDE.md). Configure from a clean build directory when testing, since options and `CXXFLAGS` are cached and a stale cache will hide the effect of your change.
