# Components and release preparation

WingTouch 0.3.1 — B4rn3y.
WingTouch itself is proprietary software governed by `LICENSE.txt` and `EULA.txt`; Copyright © 2026 B4rn3y. All rights reserved. Users retain ownership of their original user-created panels, Home Gadgets, layouts, presets, notes and similar project data as described in the WingTouch license.
This file inventories third-party components and source references and does not override their original licenses or service terms.

| Component | Use | Notice / source |
| --- | --- | --- |
| websockets 16.0 | GSX Remote API transport; pure-Python package bundled in `vendor/websockets` | BSD 3-Clause; `licenses/websockets.txt`; https://websockets.readthedocs.io/en/stable/project/license.html |
| QR Code Generator for JavaScript, Kazuhiko Arase | Local tablet QR generation | MIT; `licenses/QR-MIT.txt`; https://github.com/kazuhikoarase/qrcode-generator |
| FlyByWire documentation/catalog snapshots | A32NX / A380X telemetry definitions and provenance | GPLv3 as supplied; `catalog-sources/FBW-LICENSE.txt`, source snapshots and build scripts retained |
| Natural Earth 1:110m Admin 0 geometry | Simplified local fallback world/country outline for SimBrief Route Map | Public domain; simplified derivative in `web/world-110m.js`; https://www.naturalearthdata.com/about/terms-of-use/ |
| Natural Earth 1:50m land/lakes/Admin 0 boundaries | Detailed local geography layer for full + Home SimBrief Route Map views | Public domain; release build generates `web/world-detail.js` from pinned Natural Earth v5.1.2 GeoJSON; https://www.naturalearthdata.com/about/terms-of-use/ |
| CPython 3.13 runtime / standard library | Compiled Windows standalone runtime | PSF license stack; `licenses/Python-3.13.txt`; https://docs.python.org/3.13/license.html |
| OpenSSL 3.x | TLS/crypto runtime carried by CPython when present | Apache-2.0; `licenses/OpenSSL-Apache-2.0.txt` |
| libffi | CPython FFI runtime when present | libffi license; `licenses/libffi.txt` |
| Inno Setup 7.1.0 | Windows installer/uninstaller engine | Inno Setup License; `licenses/Inno-Setup-7.1.0.txt`; current upstream commercial-use guidance: https://jrsoftware.org/ishelp/topic_purchase.htm |
| Nuitka 4.2.1 | Windows compiler, build-time only | AGPLv3 + Nuitka Runtime Library Exception; not an end-user runtime dependency; https://github.com/Nuitka/Nuitka/blob/develop/LICENSE-RUNTIME.txt |
| jsdom 26.1.0 | Automated browser tests only | MIT; declared in `tests/package.json`; `node_modules` is not shipped |
| Microsoft Visual C++ runtime | Native DLLs selected by the final standalone build when present | Microsoft redistributable terms; exact final files must be audited from the produced Windows artifact |
| Microsoft Flight Simulator / SimConnect | External simulator interface | No Microsoft SimConnect DLL or simulator binary redistributed; WingTouch discovers the user-installed library |
| FSDreamTeam GSX Pro / Couatl Remote API | Optional external integration | No GSX Pro code, artwork or binaries redistributed; protocol references in `catalog-sources/gsx-pro-remote-api-source.json` |
| SimBrief / Navigraph | Optional external latest-OFP service and OFP-hosted briefing images | Network integration only; no SimBrief/Navigraph software or protected assets redistributed |
| AviationWeather.gov | External METAR/station data source | Network integration only; no service software/dataset bundled |
| FAA d-TPP | External terminal-procedure metadata/PDF source for Charts | Official FAA network source fetched on demand; metadata/PDFs are not bundled or mirrored |
| GitHub Releases API | Public WingTouch update metadata/download source | Public release metadata only; no end-user GitHub token/account required and no usage telemetry is sent |
| Device fonts | UI text rendering | No font files bundled by WingTouch |

## Additional notices

The bundled A32NX and A380X simulation checklist presets are
WingTouch-authored data informed by public FlyByWire references.
They are not official FlyByWire checklists.

FlyByWire Simulations is not affiliated with or endorsing WingTouch.

The applicable third-party license texts are included with WingTouch
in the `licenses` directory where required.
