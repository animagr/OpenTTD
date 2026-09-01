# .github/ — CI, release automation and lint scripts

Two dozen workflows plus five Python helpers. **None of this runs on this fork** — the workflows need OpenTTD's secrets and self-hosted actions, and nothing here is submitted upstream anyway. It is still worth knowing what they check: these are the invariants upstream holds its own code to, and this fork keeps merging that code.

## The checks that gate a pull request

| Workflow | What it enforces |
| --- | --- |
| `ci-build.yml` | Umbrella job fanning out to `ci-linux`, `ci-windows`, `ci-macos`, `ci-mingw`, `ci-emscripten`. Builds and runs `ctest`, including the [regression suites](../regression/CLAUDE.md) |
| `commit-checker.yml` | Commit message grammar, via `OpenTTD/OpenTTD-git-hooks`. **The most common reason a PR fails validation** — see the commit format in [../CLAUDE.md](../CLAUDE.md) |
| `rebase-checker.yml` | The branch must be rebased on current `master`, not merged |
| `docs-checker.yml` | Builds Doxygen before and after and fails on **new** warnings. `sort_doxygen_warnings.py` normalises the ordering so the diff is meaningful |
| `file-descriptions.yml` | Runs `file-descriptions.py` — every source file needs a `@file` annotation that Doxygen recognises and that matches the style rules |
| `script-missing-mode-enforcement.yml` | Runs `script-missing-mode-enforcement.py` — see [../src/script/CLAUDE.md](../src/script/CLAUDE.md) |
| `unused-strings.yml` | Runs `unused-strings.py` against [../src/lang/](../src/lang/CLAUDE.md) |
| `codeql.yml` | Static analysis, configured by [codeql/codeql-config.yml](codeql/codeql-config.yml) |

Five build platforms means a change that only compiles under MSVC will fail. MinGW and Emscripten in particular catch assumptions about compiler extensions and platform APIs.

## The lint scripts, and what they really check

- **`file-descriptions.py`** — a `@file` block is not optional decoration: without one, Doxygen documents *nothing* in that file. The script also checks the description reads as a sentence. Only two generated templates are exempt.
- **`unused-strings.py`** — heuristic by necessity, because OpenTTD often references the first string of a run and indexes forward from it. Read its output, do not act on it blindly.
- **`script-missing-mode-enforcement.py`** — any script API function calling `ScriptObject::Command` or `ScriptObject::GetCompany` must carry an `Enforce*Mode*` macro.
- **`changelog.py`** — assembles release notes from commit messages, which is *why* the commit grammar is enforced.
- **`sort_doxygen_warnings.py`** — support for `docs-checker`.

## Release and publish workflows

`release.yml` orchestrates `release-{linux,macos,windows,source,docs,windows-store}.yml`, then `upload-{cdn,steam,gog,windows-store}.yml`. `preview*.yml` builds the Emscripten web preview for a PR. `ci-nightly.yml` runs the extra architectures nightly.

All of these depend on repository secrets and signing material this fork does not have. Do not try to run them here, and do not modify them expecting to test the result.

## Other contents

`ISSUE_TEMPLATE/` (bug and crash forms), `PULL_REQUEST_TEMPLATE.md`, `dependabot.yml`, `FUNDING.yml`, and `install-doxygen/` — a composite action pinning the Doxygen version, so that the before/after warning comparison is not confounded by a version change.

## Editing anything here

CI changes take the `Codefix` keyword ("CI changes" is listed under it explicitly) and usually a `[CI]` component: `Codefix: [CI] Pin Doxygen version`.
