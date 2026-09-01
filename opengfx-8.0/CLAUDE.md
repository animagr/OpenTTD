# opengfx-8.0/ — the graphics base set (local addition, not upstream)

**Not part of the OpenTTD source tree.** This directory and the `opengfx-8.0.tar` next to it were downloaded into the working copy so this fork's builds have graphics to run with. They are untracked, and they should stay that way — never `git add` them, and never include them in anything proposed upstream.

## What it is

[OpenGFX](https://github.com/OpenTTD/OpenGFX) 8.0 (released 3 January 2026), the free 8bpp base graphics set that replaces the original Transport Tycoon Deluxe artwork. OpenTTD will not start without *some* base graphics set; this is the one that does not require owning TTD.

| File | Contents |
| --- | --- |
| `opengfx.obg` | Base-set metadata — name, version 9499, DOS palette, 8bpp blitter, and a description in every supported language |
| `ogfx1_base.grf` | The main sprite set |
| `ogfxc_arctic.grf`, `ogfxh_tropical.grf`, `ogfxt_toyland.grf` | Per-climate sprites |
| `ogfxe_extra.grf` | The extra sprites OpenTTD itself needs |
| `ogfxi_logos.grf` | Company logos |
| `readme.txt`, `changelog.txt`, `license.txt` | Upstream documentation; GPLv2 |

The `.tar` is the same content unextracted. OpenTTD reads uncompressed tars directly and treats each as its own search root, so **the tar is the preferred form** — it keeps the base set as one self-contained unit.

## Installing it

Copy the tar (or the extracted folder) into the `baseset/` subdirectory of an OpenTTD data directory. On Windows that is:

```
C:\Users\<username>\Documents\OpenTTD\baseset\
```

The `baseset/` directory next to a built binary also works, which is convenient for testing a local build. [../docs/directory_structure.md](../docs/directory_structure.md) has the full search order.

Then start OpenTTD → **Game Options** → pick OpenGFX under *Base graphics set*. If the game only shows a missing-graphics bootstrap screen, the set is not where OpenTTD is looking.

You will likely also want a sound set (OpenSFX) and a music set (OpenMSX); both install into the same `baseset/` directory, and both are available in-game through **Check Online Content**, which is generally easier than downloading by hand.

## Do not edit anything here

These are release artifacts of a separate project under its own GPLv2 copy in `license.txt`. Rebuilding a sprite means working in the OpenGFX repository, not here — and OpenTTD's *own* sprites, the GUI icons and overlays, are a different thing entirely and live in [../media/baseset/](../media/CLAUDE.md).

To update, download a newer release from [the official downloads](https://www.openttd.org/downloads/opengfx-releases/latest.html) and replace the directory; there is no in-place upgrade. Doing it through the in-game content service instead is usually simpler, and puts the set in the same place.
