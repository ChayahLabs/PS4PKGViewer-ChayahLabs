# Third-Party Notices

PS4PKGViewer was originally created by **LMAN <LeecherMan>**.

This repository contains compatibility work and documentation maintained by **ChayahLabs**.

## LibOrbisPkg / PkgTool

The compatibility fallbacks use **[LibOrbisPkg / PkgTool](https://github.com/maxton/LibOrbisPkg)**, originally developed by **[Maxton](https://github.com/maxton)** and contributors.

LibOrbisPkg is distributed by its upstream project under the **GNU Lesser General Public License v3.0 (LGPL-3.0)**. The upstream source code, license text, project history and contributor information are available from the original repository:

https://github.com/maxton/LibOrbisPkg

ChayahLabs does not claim authorship of LibOrbisPkg / PkgTool. All copyright, attribution and license terms belonging to Maxton and the upstream contributors remain applicable to their work.

The v1.6.6 binary distribution includes:

- `LICENSE-LibOrbisPkg.txt` — the upstream LibOrbisPkg license text.
- `ChayahLabs.Runtime/LibOrbisPkg.Core.dll` — the external and replaceable LibOrbisPkg runtime used by the v1.6.6 PFS-size metadata probe.

Keeping `LibOrbisPkg.Core.dll` external in `ChayahLabs.Runtime` allows the library to remain independently replaceable from the PS4PKGViewer executable and compatibility bridge.

The v1.6.5 secondary ICON0 fallback remains embedded in `ChayahLabs.PS4IconFallback.dll` and is materialized only when that fallback is required. Its upstream LibOrbisPkg attribution and LGPL-3.0 terms remain applicable.

## ORBISPatches

**ORBISPatches** is used as an external update-information resource. Its project, service and data remain under the control of their respective maintainers.

## Trademarks

PlayStation, PS4 and related names and trademarks are property of Sony Interactive Entertainment Inc. and/or their respective owners.

This project is not affiliated with or endorsed by Sony Interactive Entertainment.