# src/3rdparty/ — vendored libraries

**Do not edit anything in here.** These are upstream projects copied into the tree, each under its own license — see [README.licensing](README.licensing) and the `LICENSE*` file in each subdirectory. They are explicitly *not* under OpenTTD's GPLv2.

| Directory | Library | Used for |
| --- | --- | --- |
| [catch2/](catch2/) | Catch2 v2.13.10 | Unit test framework — [../tests/](../tests/CLAUDE.md) |
| [fmt/](fmt/) | fmtlib | All string formatting. `safeguards.h` bans `sprintf`, so this is the replacement |
| [icu/](icu/) | ICU layout shims | Right-to-left script handling, alongside HarfBuzz |
| [md5/](md5/) | MD5 | Base-set and content checksums |
| [monocypher/](monocypher/) | Monocypher | X25519 key exchange for the multiplayer handshake — [../network/](../network/CLAUDE.md) |
| [nlohmann/](nlohmann/) | nlohmann/json | JSON for the game coordinator, survey and social integration |
| [opengl/](opengl/) | `glext.h` etc. | OpenGL headers for the OpenGL video backend |
| [openttd_social_integration_api/](openttd_social_integration_api/) | Social API headers | Discord/Steam presence plugins |
| [squirrel/](squirrel/) | Squirrel VM | The language AIs and GameScripts are written in — [../script/](../script/CLAUDE.md) |

Between them these are the largest files in the repository (`nlohmann/json.hpp` at ~21.6k lines, `catch.hpp` at ~14.8k, `glext.h` at ~12.3k). They also contain the codebase's only dependency cycle, among fmt's `base.h` / `format-inl.h` / `format.h` — that is upstream's design, not something to fix.

## If a change is genuinely needed

Upgrade the vendored copy wholesale from the library's own release rather than patching in place: a local edit is invisible to the next person who syncs the directory and will be silently lost. If a patch truly cannot be avoided, it needs a clearly marked comment saying what was changed and why, and upstream would want it reported to the library's maintainers too.

The exception is the `CMakeLists.txt` in each directory, which is OpenTTD's own build glue and is expected to be maintained here.
