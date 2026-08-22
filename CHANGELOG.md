# Changelog

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
- Public distribution now contains exactly:
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
