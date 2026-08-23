# Changelog

## v1.6.6 — ChayahLabs List Contents Size Accuracy Update

### List Contents size accuracy
- Fixed affected compatible PS4 Fake PKGs whose `Image0` files could incorrectly appear as `0 Bytes`.
- Preserved every existing non-zero size reported by the normal package-listing path.
- Added an exact inner-PFS path lookup only for zero-size file candidates.
- Replaces a false zero only when the exact PFS entry proves a logical size greater than zero.
- Genuine zero-byte files remain zero.
- Missing or inaccessible PFS metadata preserves the original result.
- No `compressed_size` fallback is used.

### Decrypted-size correction
- Corrected `Properties > Decrypted-size` after valid List Contents size corrections.
- The decrypted aggregate is recomputed from the final `PkgCabinet` file state.
- Repeated execution is idempotent and does not repeatedly add size deltas.

### PFS size metadata fallback
- Added `ChayahLabs.PS4SizeFallback.dll`.
- Added `ChayahLabs.PS4PfsSizeProbe` under `ChayahLabs.Runtime`.
- Uses LibOrbisPkg `PfsReader.GetAllFiles()` logical file sizes for exact-path matches.
- Added an in-memory package-size cache for fast repeated List Contents access.
- The fallback is silent and read-only.
- No extraction or DRM/protection bypass behavior was introduced.

### Validation
- Hulu / CUSA00131: 11 false zero-size files corrected.
- FPKGi v1.10.0: genuine zero-byte `Media/boot.config` preserved.
- CUSA49956 sample: 157 false zero-size files corrected.
- WatchESPN / CUSA05214: existing valid non-zero sizes remained unchanged.

### Runtime and distribution
- Moved the PFS size-probe support files into `ChayahLabs.Runtime`.
- Kept `LibOrbisPkg.Core.dll` external and replaceable.
- Added `LICENSE-LibOrbisPkg.txt` and expanded `THIRD_PARTY_NOTICES.txt` to the portable binary distribution.
- `PS4PKGViewer.bin` is not distributed; it is generated locally as user configuration when needed.
- Final public archive is a true RAR 4.x archive with a native archive comment.
- Updated visible version, About, AssemblyVersion, FileVersion, ProductVersion and Readme to `1.6.6`.

### Retained compatibility
- Retained all v1.6.5 ICON0 compatibility work.
- Retained all v1.6.4 List Contents, PFS crypto, update metadata and `SYSTEM_VER` compatibility work.

## v1.6.5 — ChayahLabs ICON0 Compatibility Update

### ICON0 compatibility
- Fixed missing package icons in some rebuilt or non-standard PS4 PKGs.
- Fixed compatibility with packages affected by the legacy `ENTRY_NAMES` positional association behavior.
- Added a direct MetaEntry-based `ICON0` fallback.
- Preserved the original icon-loading path when the legacy icon data is already valid.
- Prefer `ICON0_PNG` entry ID `0x1200`; compatible `0x1201..0x121F` variants are also supported.
- Reads compatible unencrypted icon data directly using package `DataOffset` / `DataSize`.
- Validates package bounds and PNG/JPEG signatures before using fallback icon data.
- Avoids external PkgTool processes when the direct metadata path succeeds.

### Self-contained secondary ICON0 fallback
- Embedded the secondary LibOrbisPkg / PkgTool 0.2.231.2 runtime inside `ChayahLabs.PS4IconFallback.dll`.
- Removed the need to distribute an external `ChayahPkgTool` folder.
- The embedded runtime is materialized under Windows TEMP only if the secondary ICON0 fallback is actually required.
- RC3 build validation verified all five embedded runtime files against their source SHA256 values.

### Regression validation
- Validated direct ICON0 loading with:
  - Store-R2-PS5.pkg
  - Hulu CUSA00131
  - WatchESPN CUSA05214
  - PS5_LAPY20011_v1.04.pkg
- Verified normal packages continue to use the original icon path (`Legacy icon valid; fallback skipped`).
- Verified Hulu `List Contents` behavior remains functional.
- Preserved `PS4PKGViewer.dat` behavior from the validated v1.6.4 build.

### Versioning and distribution
- Updated visible version to PS4PKGViewer v1.6.5.
- Updated AssemblyVersion, FileVersion and ProductVersion to `1.6.5.0`.
- Updated and embedded the v1.6.5 Readme.
- Public distribution contains:
  - `PS4PKGViewer.exe`
  - `PS4PKGViewer.dat`
  - `PS4UpdateInfo.ps1`
  - `Readme.txt`
  - `ChayahLabs.PS4IconFallback.dll`

## v1.6.4 — ChayahLabs Compatibility Update

### Package compatibility
- Improved List Contents support for newer and rebuilt PS4 packages.
- Added LibOrbisPkg / PkgTool 0.2.231.2 fallback support for Fake PKGs.
- Preserved the normal ps4pub path for packages it can already enumerate.
- Added shared-read PKG access for the compatibility fallback.
- Added reconstruction of `Sc0` entries and conversion of `/uroot/...` paths to `Image0/...`.

### PFS crypto compatibility
- Added automatic retry with legacy PFS key derivation when a package exposes the newer crypto flag but the first PFS mode is invalid.
- Fixed `inode 0 is corrupt` and empty List Contents failures affecting compatible FPKGs.
- The crypto fallback is silent and requires no manual environment variable or user intervention.

### SYSTEM_VER
- Fixed status-bar firmware formatting for PS4 firmware 10.00 and newer.
- Corrected values such as:
  - `0x07500000` → `System v7.50`
  - `0x13508000` → `System v13.50`
- The update-check firmware requirement remains separate from the `SYSTEM_VER` of the loaded PKG.

### Update features
- Replaced the discontinued Octolus service with ORBISPatches.
- Added Sony update XML / manifest metadata.
- Added Copy Links for Sony update PKG URLs.
- Added Save Updates for XML and manifest metadata.

### Branding and documentation
- Updated visible version to PS4PKGViewer v1.6.4.
- Updated About information and credits.
- Updated footer credits to LMAN & ChayahLabs.
- Unified the bundled Readme under v1.6.4.
- Added acknowledgements and bug / feature-request guidance.

## v1.0–v1.5

Original PS4PKGViewer releases by LMAN <LeecherMan>.