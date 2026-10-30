# Lies of P Enemy & Item Randomizer — v1.4.2 (version-independent helper)

FiendBusa's Lies of P Enemy & Item Randomizer, updated so it runs on the
current game build: **LOP-Win64-Shipping v1.14.0.0** (build 25227444), and
keeps working on future game versions: the helper's hook anchor points are
found by **runtime signature scanning** (1.4.2) instead of hard-coded RVAs.

## What is in this repo

| Path | What it is |
|---|---|
| `dxgi.dll` | The mod's proxy DLL (unchanged from 1.4.1) |
| `mods/LOP-RANDO-DLL-HELPER.dll` | Helper DLL that installs the runtime hooks — rebuilt in 1.4.2 with signature scanning: it locates both hook sites in the game image at startup, no hard-coded RVAs |
| `_backup_original_1_4_1/` | Untouched v1.4.1 helper DLL, kept for reference |
| `PATCH NOTES.txt` | Changelog — `1.4.1b` documents the RVA port for game v1.14.0.0; `1.4.2` documents the signature-scanning rebuild (byte patterns, fail-open policy, hashes) |

The large randomizer exe and the distribution zips are intentionally **not**
stored in git (GitHub file-size limits) — download them from the
**Releases** page of this repo instead.

## Install

1. Download the release zip (e.g. `lop-randomizer-1.4.2.zip`) from Releases.
2. Extract it where you previously installed v1.4.x: the mod's `dxgi.dll` must
   sit next to the game executable (`<game>\LiesofP\Binaries\Win64\`), with the
   `mods\` folder beside it. Upgrading from 1.4.1/1.4.1b: just overwrite
   `mods\LOP-RANDO-DLL-HELPER.dll` with the one from this repo/release.
3. Run `LiesOfPEnemyRandomizer.exe` to generate (or re-generate) a randomized
   layout, then launch the game.

Notes:
- Only one `dxgi.dll` proxy can be loaded per directory. If you also run other
  `dxgi.dll`-based loaders (UE4SS etc.), arrange co-existence the same way you
  did for v1.4.1 — nothing changed in that regard.
- About 5 s after the game starts, the helper writes
  `mods\LOP-RANDO-DLL-HELPER.log` (next to the DLL) listing the pattern hits
  and the hooks it installed. If something does not work, attach that log
  when reporting the issue.
- Each hook installs only when its byte pattern matches exactly once in the
  game exe; otherwise that hook is skipped (fail-open) and the game runs
  unmodded for that feature.
- See `PATCH NOTES.txt` for the exact patterns, verification setup and hashes.
- The modified helper source tree (signature-scanner build) is attached to
  the release page as a source zip.

## Credits

Original mod, randomizer and helper DLL sources: **FiendBusa** (v1.4.1, Sep 2025).
Compatibility update (helper hook re-anchoring for game v1.14.0.0): community, 2026.
Signature-scanning, version-independent helper rebuild: community, 2026.
