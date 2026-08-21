# Changelog

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
