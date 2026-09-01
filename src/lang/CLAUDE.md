# src/lang/ — the language files

66 `.txt` language files. **Only [english.txt](english.txt) is edited by hand.** It is the master; every other file in this directory is owned by [Eints](https://translator.openttd.org/), OpenTTD's web translator, which syncs into the repository nightly (those are the `Update: Translations from eints` commits).

Full policy in [../../docs/eints.md](../../docs/eints.md). Format reference in [../../docs/compiling_lang_files.md](../../docs/compiling_lang_files.md).

## Never touch the translations

This is the rule that surprises people. Whatever you do to `english.txt`, leave the other 65 files alone — even if you speak the language, and **even when the build emits warnings about them**. Eints reconciles everything on the next nightly sync.

What the sync does for each kind of change:

| Change to `english.txt` | What happens to translations |
| --- | --- |
| Reword a string, same meaning | Marked "outdated"; translators re-check |
| Add, change or remove parameters | Marked "invalid"; removed from git until fixed, so the warnings stop after the sync |
| Change a string's meaning entirely | **Rename the `STR_…` identifier** — remove the old, add a new. Eints then discards the stale translations rather than leaving misleading ones |
| Add a new string | Nothing; place it in `english.txt` where it fits with its neighbours |
| Remove an unused string | Eints removes the translations |
| Reorder strings | Eints reorders every translation to match |
| Edit `#` comments | Nothing |

Translation-only PRs against upstream are closed as a matter of policy; typo reports go to the issue tracker so the language team can decide.

## File format

A header block of `##` directives, then `##id`-anchored sections of `STR_IDENTIFIER : text` lines:

```
##name English (UK)
##isocode en_GB
##plural 0
##textdir ltr
##digitsep ,
##decimalsep .
##grflangid 0x01

##id 0x0000
STR_NULL                                                        :
```

The identifier column is space-padded to a fixed width — match the surrounding lines. Placeholders in the text (`{STRING}`, `{NUM}`, `{COMMA}`, `{RAW_STRING}`, gender and plural forms) are part of the contract with the calling code; changing them is the "invalid" case above.

## How it becomes code

`strgen` (built from [../strgen/](../strgen/)) compiles `english.txt` into two things at build time:

- `<build>/generated/table/strings.h` — the `STR_…` enum that C++ includes as `"table/strings.h"`.
- `*.lng` binary files, one per language, shipped in the `lang/` data directory.

So a new string is available to C++ as soon as it exists in `english.txt` and the build has re-run. There is nothing to register by hand, but [CMakeLists.txt](CMakeLists.txt) does list every language file explicitly — a genuinely new language needs adding there (and needs an issue upstream first).

## Unused strings

[../../.github/unused-strings.py](../../.github/unused-strings.py) runs in CI and reports `STR_` entries that are defined but no longer referenced. It is heuristic — OpenTTD frequently references only the first string of a run and does arithmetic to reach the rest, and the script tries to model that — so treat its output as a prompt to check, not proof. Deleting a string that is reached by offset from another will break the game at runtime with no compile error.
