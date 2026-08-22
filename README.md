# PS4PKGViewer v1.6.5 — ChayahLabs ICON0 Compatibility Update

PS4PKGViewer is a Windows utility originally created by **LMAN <LeecherMan>** for viewing information and contents from PlayStation 4 PKG files.

This repository documents and distributes the **ChayahLabs compatibility update for PS4PKGViewer v1.6.5**.

> Special thanks to **LMAN <LeecherMan>**, the original creator of PS4PKGViewer. Without his work, this compatibility update would not have been possible.

## Current release

**PS4PKGViewer v1.6.5 — ChayahLabs ICON0 Compatibility Update**

- Release: https://github.com/ChayahLabs/PS4PKGViewer-ChayahLabs/releases/tag/v1.6.5
- Archive: `PS4PKGViewer.v1.6.5-LMAN_ChayahLabs.rar`
- SHA256: `6411FB19E55AC894DCDB34D5DA42EF93262681D0F2A85AD92713D19DC97783E6`

## What's new in v1.6.5

- Fixed missing package icons in some rebuilt or non-standard PS4 PKGs.
- Fixed compatibility with packages affected by the legacy `ENTRY_NAMES` positional association behavior.
- Added a fast direct `ICON0` metadata-entry fallback.
- Preserved the original icon-loading path for packages that already work.
- Uses direct package metadata lookup for `ICON0_PNG` (`0x1200`) and supported variants when the legacy association is invalid.
- Reads compatible unencrypted icon data directly from its package `DataOffset` / `DataSize`, avoiding external PkgTool processes in the normal fallback path.
- Embedded the secondary **LibOrbisPkg / PkgTool 0.2.231.2** ICON0 runtime inside `ChayahLabs.PS4IconFallback.dll`.
- The secondary ICON0 runtime is materialized to Windows TEMP only when actually required; no external `ChayahPkgTool` folder is distributed.
- Retained the existing v1.6.4 **List Contents**, PFS crypto, update metadata and `SYSTEM_VER` compatibility work.
- Updated About, AssemblyVersion, FileVersion, ProductVersion and Readme to v1.6.5.

## Retained v1.6.4 compatibility work

- Improved **List Contents** support for newer and rebuilt PS4 packages.
- Added a **LibOrbisPkg / PkgTool 0.2.231.2 compatibility fallback** for Fake PKGs.
- Added automatic fallback for packages that expose the newer PFS crypto flag but still require the legacy PFS key derivation.
- Fixed `inode 0 is corrupt` and empty List Contents failures affecting compatible FPKGs.
- Fixed `SYSTEM_VER` formatting for PS4 firmware versions **10.00 and newer**.
- Replaced the discontinued Octolus integration with **ORBISPatches**.
- Added Sony update metadata support, **Copy Links** and **Save Updates**.

## Requirements

- Microsoft .NET Framework 4.0 or newer
- Microsoft .NET 8 Runtime (x64)
- PowerShell 7 (`pwsh.exe`)

## Distribution files

The v1.6.5 binary release contains exactly:

```text
PS4PKGViewer.v1.6.5-LMAN_ChayahLabs/
├── PS4PKGViewer.exe
├── PS4PKGViewer.dat
├── PS4UpdateInfo.ps1
├── Readme.txt
└── ChayahLabs.PS4IconFallback.dll
```

`ChayahPkgTool` is not distributed as an external folder. The secondary ICON0 fallback runtime is embedded in `ChayahLabs.PS4IconFallback.dll` and is extracted to Windows TEMP only if that fallback is needed.

## Download

Use the **Releases** section of this repository to download the packaged build.

The release archive is distributed as:

```text
PS4PKGViewer.v1.6.5-LMAN_ChayahLabs.rar
```

SHA256:

```text
6411FB19E55AC894DCDB34D5DA42EF93262681D0F2A85AD92713D19DC97783E6
```

The release also includes a `.sha256.txt` asset for verification.

## Bugs, compatibility reports and improvements

Bug reports, compatibility problems, new ideas and feature suggestions are welcome.

Please open a **GitHub Issue** and include, when possible:

- Title ID / Content ID
- Base game or update
- Official PKG or Fake PKG
- `SYSTEM_VER`
- PS4PKGViewer error message
- Relevant `%TEMP%\PS4PKGViewer_IconFallback.log` output for icon problems
- Relevant `%TEMP%\PS4PKGViewer_ChayahFallback.log` output for List Contents / package fallback problems
- Steps needed to reproduce the issue

Feature requests and compatibility improvements are also welcome.

## Acknowledgements

Special thanks to:

- **LMAN <LeecherMan>** — original author of PS4PKGViewer.
- **Maxton** and the contributors to **LibOrbisPkg / PkgTool**.
- **ORBISPatches** and its contributors.
- Everyone involved in PS4 package research, documentation, development, testing and community support.
- Users who report compatibility issues and suggest improvements.

## Project history

The original PS4PKGViewer releases were created by LMAN.

The **v1.6.4 ChayahLabs compatibility update** focused on newer/rebuilt package listing, PFS crypto compatibility, update metadata and newer firmware-version formatting.

The **v1.6.5 ChayahLabs ICON0 Compatibility Update** adds a dedicated compatibility path for packages whose legacy `ENTRY_NAMES` positional association can point `icon0.png` at the wrong package entry, while preserving the original behavior for packages that already work.

See [CHANGELOG.md](CHANGELOG.md) for the detailed changes.

## Legal / licensing notice

This repository contains compatibility work and documentation maintained by ChayahLabs.

PS4PKGViewer and any third-party components remain the property of their respective authors and copyright holders. See [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).

No affiliation with Sony Interactive Entertainment is claimed or implied.

## Credits

**Original author:**  
LMAN <LeecherMan> (2018)

**Compatibility updates:**  
ChayahLabs (2026)

https://github.com/ChayahLabs

## Project documentation

- [Changelog](CHANGELOG.md)
- [Contributing](CONTRIBUTING.md)
- [Support](SUPPORT.md)
- [Security policy](SECURITY.md)
- [Third-party notices](THIRD_PARTY_NOTICES.md)
