# PS4PKGViewer v1.6.4 — ChayahLabs Compatibility Update

PS4PKGViewer is a Windows utility originally created by **LMAN <LeecherMan>** for viewing information and contents from PlayStation 4 PKG files.

This repository documents and distributes the **ChayahLabs compatibility update for PS4PKGViewer v1.6.4**.

> Special thanks to **LMAN <LeecherMan>**, the original creator of PS4PKGViewer. Without his work, this compatibility update would not have been possible.

## What's new in v1.6.4

- Improved **List Contents** support for newer and rebuilt PS4 packages.
- Added a **LibOrbisPkg / PkgTool 0.2.231.2 compatibility fallback** for Fake PKGs.
- Added automatic fallback for packages that expose the newer PFS crypto flag but still require the legacy PFS key derivation.
- Fixed `inode 0 is corrupt` and empty List Contents failures affecting some FPKGs.
- Fixed `SYSTEM_VER` formatting for PS4 firmware versions **10.00 and newer**.
  - Example: `0x13508000` is now displayed correctly as `System v13.50` instead of `System v1.35`.
  - Older values such as `0x07500000` continue to display correctly as `System v7.50`.
- Replaced the discontinued Octolus integration with **ORBISPatches**.
- Added Sony update metadata support.
- Added **Copy Links** for Sony update PKG URLs.
- Added **Save Updates** for update XML and manifest metadata.
- Updated About information, credits, copyright and Readme.

## Requirements

- Microsoft .NET Framework 4.0 or newer
- Microsoft .NET 8 Runtime (x64)
- PowerShell 7 (`pwsh.exe`)

## Distribution files

The binary release contains:

```text
PS4PKGViewer.v1.6.4-LMAN_ChayahLabs/
├── PS4PKGViewer.exe
├── PS4PKGViewer.dat
├── PS4UpdateInfo.ps1
└── Readme.txt
```

## Download

Use the **Releases** section of this repository to download the packaged build.

The release archive is distributed as:

```text
PS4PKGViewer.v1.6.4-LMAN_ChayahLabs.rar
```

## Bugs, compatibility reports and improvements

Bug reports, compatibility problems, new ideas and feature suggestions are welcome.

Please open a **GitHub Issue** and include, when possible:

- Title ID / Content ID
- Base game or update
- Official PKG or Fake PKG
- `SYSTEM_VER`
- PS4PKGViewer error message
- Relevant `%TEMP%\PS4PKGViewer_ChayahFallback.log` output
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

The **v1.6.4 ChayahLabs compatibility update** focuses on maintaining compatibility with newer/rebuilt PKGs, improving List Contents behavior, preserving support for existing packages, and correcting newer firmware-version formatting.

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
