# PS4PKGViewer v1.6.6 — ChayahLabs List Contents Size Accuracy Update

PS4PKGViewer v1.6.6 is the third ChayahLabs compatibility release after v1.6.4 and v1.6.5.

## Main change

Some compatible PS4 Fake PKGs could expose valid files in **Extra > List Contents** with a reported size of `0 Bytes`, even though those files had real logical content inside the package PFS.

v1.6.6 adds a conservative, read-only correction path:

1. Existing non-zero sizes are left untouched.
2. Only zero-size **file** entries become candidates.
3. The exact package-relative path is looked up in the inner PFS metadata.
4. A zero is replaced only when that exact PFS entry reports a logical size greater than zero.
5. A genuine PFS size of zero remains zero.
6. Missing or inaccessible PFS metadata leaves the original Viewer result unchanged.

No compressed-size guessing is used.

## Decrypted-size

`Properties > Decrypted-size` is now recomputed from the final logical file list after any valid corrections, avoiding stale totals and repeated-delta accumulation.

## Performance

The PFS-size results are cached in memory for repeated access to the same package. The fallback remains silent and read-only.

## Validation

The implementation was validated with:

- **Hulu / CUSA00131** — 11 false zero-size files corrected.
- **FPKGi v1.10.0** — genuine zero-byte `Media/boot.config` preserved.
- **CUSA49956 sample** — 157 false zero-size files corrected.
- **WatchESPN / CUSA05214** — existing valid sizes remained unchanged.

## Portable runtime

The v1.6.6 size-accuracy support files are grouped under:

```text
ChayahLabs.Runtime/
```

This folder contains the small PFS metadata probe and the external `LibOrbisPkg.Core.dll` runtime.

Keep the complete release folder together.

`PS4PKGViewer.bin` is not part of the distribution. It is a small user-configuration file created locally by PS4PKGViewer when needed.

## Retained fixes

v1.6.6 retains:

- v1.6.5 ICON0 compatibility work.
- v1.6.4 List Contents/PFS crypto compatibility.
- `SYSTEM_VER` formatting for newer PS4 firmware versions.
- ORBISPatches/Sony update metadata support.
- Copy Links and Save Updates functionality.

## Requirements

- Windows x64
- Microsoft .NET Framework 4.0 or newer
- Microsoft .NET 8 Runtime (x64)
- PowerShell 7 (`pwsh.exe`)

## Download

Release:

https://github.com/ChayahLabs/PS4PKGViewer-ChayahLabs/releases/tag/v1.6.6

Archive:

```text
PS4PKGViewer.v1.6.6-LMAN_ChayahLabs.rar
```

The public archive is a true **RAR 4.x** archive with a native archive comment.

SHA256:

```text
44A0490FD8D3DD7B9D743651CF1D535918BAE77427DFB1FC8274DF438FCBC762
```

A matching `.sha256.txt` asset is included with the GitHub release.

## Credits

**Original author:** LMAN <LeecherMan> (2018)

**Compatibility updates:** ChayahLabs (2026)

Special thanks to **Maxton** and the **LibOrbisPkg / PkgTool** contributors, **ORBISPatches**, and everyone involved in PS4 package research, documentation, testing and compatibility reporting.

LibOrbisPkg remains subject to its upstream **LGPL-3.0** terms.