# Lies of P Enemy & Item Randomizer — v1.4.1b (community compatibility update)

FiendBusa's Lies of P Enemy & Item Randomizer v1.4.1, updated so it runs on the
current game build: **LOP-Win64-Shipping v1.14.0.0** (build 25227444).

## What is in this repo

| Path | What it is |
|---|---|
| `dxgi.dll` | The mod's proxy DLL (unchanged from 1.4.1) |
| `mods/LOP-RANDO-DLL-HELPER.dll` | Helper DLL that installs the runtime hooks — updated for game v1.14.0.0 |
| `_backup_original_1_4_1/` | Untouched v1.4.1 helper DLL, kept for reference |
| `PATCH NOTES.txt` | Changelog — the `1.4.1b` entry documents the compatibility update in full (old/new RVAs, byte signatures, hashes) |

The large randomizer exe and the distribution zips are intentionally **not**
stored in git (GitHub file-size limits) — download them from the
**Releases** page of this repo instead.

## Install

1. Download the release zip (e.g. `lop-randomizer-1.4.1b.zip`) from Releases.
2. Extract it where you previously installed v1.4.x: the mod's `dxgi.dll` must
   sit next to the game executable (`<game>\LiesofP\Binaries\Win64\`), with the
   `mods\` folder beside it. This update only replaces the helper DLL inside
   `mods\` — if you already have the mod installed, you can just overwrite
   `mods\LOP-RANDO-DLL-HELPER.dll` with the one from this repo/release.
3. Run `LiesOfPEnemyRandomizer.exe` to generate (or re-generate) a randomized
   layout, then launch the game.

Notes:
- Only one `dxgi.dll` proxy can be loaded per directory. If you also run other
  `dxgi.dll`-based loaders (UE4SS etc.), arrange co-existence the same way you
  did for v1.4.1 — nothing changed in that regard.
- Game v1.14.0.0 is content-neutral for the randomizer assets, so previously
  generated randomization files remain valid.
- See `PATCH NOTES.txt` for the exact hook-table changes and verification
  hashes.

## Credits

Original mod, randomizer and helper DLL sources: **FiendBusa** (v1.4.1, Sep 2025).
Compatibility update (helper hook re-anchoring for game v1.14.0.0): community,
2026.
