# src/saveload/ — savegame reading, writing and migration

Every savegame OpenTTD has ever written must still load. That constraint drives everything in this directory, and it is the reason changes here are unusually easy to get wrong.

The on-disk format is documented in [../../docs/savegame_format.md](../../docs/savegame_format.md) — outer compression container (`OTTD`/`OTTN`/`OTTZ`/`OTTX`), big-endian fields, gamma-coded lengths.

## Bumping the savegame version

`SaveLoadVersion` in [saveload.h](saveload.h) is an `enum class ... : uint16_t` whose *ordinal position* is the version number written into the file. Consequences:

- **Append only.** Add your entry immediately before `MaxVersion`, never anywhere else.
- **Never reorder or delete entries.** Doing so silently renumbers every later version and misreads every existing savegame.
- Newer entries use a descriptive label rather than a number, and document themselves in a `///<` comment carrying the numeric version and the PR:
  ```cpp
  DepotsUnderBridges, ///< Saveload version: 366, GitHub pull request: 15836\n Allow depots under bridges.
  ```
  Count the position to get the number right — the comment is not what defines it.
- `MinVersion` and `MaxVersion` bracket the enum; `MaxVersion` must stay last.

Guard version-dependent behaviour with `IsSavegameVersionBefore(SaveLoadVersion::YourEntry)` or `IsSavegameVersionBeforeOrAt(...)`. `SaveLoad` field descriptions carry their own inclusive-from / exclusive-to version range, checked by `SlIsObjectCurrentlyValid` — that is how a field is made to exist only between two versions.

## Chunk handlers

Each subsystem owns a `*_sl.cpp` with one `ChunkHandler` subclass per four-letter chunk tag:

```cpp
struct CITYChunkHandler : ChunkHandler {
    CITYChunkHandler() : ChunkHandler("CITY", ChunkType::Table) {}
    void Save() const override;
    void Load() const override;
    void FixPointers() const override;
};
static const CITYChunkHandler CITY;
static const ChunkHandlerRef town_chunk_handlers[] = { CITY, … };
extern const ChunkHandlerTable _town_chunk_handlers(town_chunk_handlers);
```

The handler table must also be referenced from the master list in [saveload.cpp](saveload.cpp), or the chunk is neither written nor read.

`FixPointers()` runs after every chunk has loaded and is where pool indices get resolved back into pointers. Anything that references another pool item belongs there, not in `Load()`.

## The `compat/` headers

[compat/](compat/) holds one `*_sl_compat.h` per subsystem, recording the **original field order** from before table headers existed:

```cpp
const SaveLoadCompat _town_supplied_sl_compat[] = {
    SLC_VAR("old_max"),
    SLC_VAR("new_max"),
    …
};
```

Modern (`ChunkType::Table`) savegames carry a self-describing header, so fields can be added or reordered freely. Old savegames do not — they are positional, and these arrays are the only record of what position meant what. **Never edit an existing entry in a compat array.** When you add a field to a `SaveLoad` description, append `SLC_NULL` / the appropriate entry only if the field also existed in the pre-table era; a genuinely new field needs no compat entry at all.

## afterload.cpp

[afterload.cpp](afterload.cpp) runs once after loading, and is where every migration lands: recomputing caches, converting old representations, fixing up state the old version did not store. It is a long chain of `if (IsSavegameVersionBefore(...))` blocks in ascending version order — add yours at the end of that sequence, and keep it there so the migrations compose correctly when loading a very old game.

`oldloader.cpp` / `oldloader_sl.cpp` handle pre-0.3.0 TTD-era savegames through a separate path entirely.

## Testing a change here

Do not trust a round-trip of your own new savegame — that only proves the writer agrees with the reader. Load an *older* savegame, ideally several versions back. [../../regression/](../../regression/) ships `.sav` fixtures, and `cmake --build build --target regression` exercises loading them.

A savegame that loads but produces subtly different state is a desync source in multiplayer; see [../../docs/desync.md](../../docs/desync.md) and the cache-checking hooks in [../cachecheck.cpp](../cachecheck.cpp).
