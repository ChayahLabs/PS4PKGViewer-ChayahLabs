# PS4PKGViewer v1.6.4 — ChayahLabs Compatibility Update

This release modernizes PS4PKGViewer compatibility while preserving the behavior of packages that already worked correctly.

Highlights:

- LibOrbisPkg / PkgTool 0.2.231.2 List Contents fallback
- Automatic PFS legacy-crypto compatibility retry
- Fix for `inode 0 is corrupt` / empty List Contents failures
- Correct PS4 `SYSTEM_VER` formatting for firmware 10.00+
- ORBISPatches integration
- Sony update metadata
- Copy Links
- Save Updates
- Updated About, credits and Readme

### Firmware formatting examples

```text
0x07500000 -> System v7.50
0x13508000 -> System v13.50
```

### Requirements

- Microsoft .NET Framework 4.0+
- Microsoft .NET 8 Runtime (x64)
- PowerShell 7

### SHA256

SHA256: `49745B7927255162ADE6EAF10C7F46C1642D3F4577E0FE609AC5EE7FD05EF93D`

### Credits

Original PS4PKGViewer by **LMAN <LeecherMan>**.

Compatibility update by **ChayahLabs**.

Thanks to Maxton and LibOrbisPkg/PkgTool contributors, ORBISPatches, researchers, testers, documenters and the wider PS4 community.

