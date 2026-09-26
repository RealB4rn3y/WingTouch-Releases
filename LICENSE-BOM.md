# WingTouch 0.3.1 — Release License BOM

This bill of materials separates components shipped to end users from build/test-only tooling.
`THIRD-PARTY-NOTICES.md` remains the human-readable notice file.

| Component | Role | Shipped? | License / notice | Evidence / handling |
| --- | --- | --- | --- | --- |
| WingTouch | Application | Yes | Proprietary (`LICENSE.txt`, `EULA.txt`) | Copyright © 2026 B4rn3y |
| CPython 3.13 | Compiled runtime | Yes | PSF License Version 2 (`licenses/Python-3.13.txt`) | `python313.dll` and stdlib/runtime files in Nuitka standalone output |
| OpenSSL 3.x | TLS/crypto runtime carried by CPython | Yes when present in Windows runtime | Apache-2.0 (`licenses/OpenSSL-Apache-2.0.txt`) | `libssl-3.dll`, `libcrypto-3.dll` |
| libffi | CPython FFI runtime | Yes when present in Windows runtime | libffi license (`licenses/libffi.txt`) | `libffi-8.dll` |
| websockets 16.0 | GSX Remote API transport | Yes | BSD 3-Clause (`licenses/websockets.txt`) | Vendored and compiled into standalone output |
| QR Code Generator for JavaScript | Browser QR generation | Yes | MIT (`licenses/QR-MIT.txt`) | `web/qrcode.js` |
| FlyByWire documentation/catalog source snapshots | Catalog provenance | Yes | GPLv3 as supplied (`catalog-sources/FBW-LICENSE.txt`) | Source snapshots/build scripts retained with the catalog |
| WingTouch A32NX/A380X checklist presets | Built-in simulation checklist data | WingTouch-authored; no third-party checklist asset bundled | References public FlyByWire documentation; existing FBW documentation notices retained | `catalog-sources/checklist-presets-source.json` records provenance and no-affiliation note |
| Natural Earth 1:110m geometry | Route-map fallback data | Yes | Public domain | Simplified derivative in `web/world-110m.js`; used only when the generated 1:50m asset is unavailable |
| Natural Earth 1:50m geometry | Detailed full + Home Route Map data | Yes | Public domain | Release build generates `web/world-detail.js` from pinned Natural Earth v5.1.2 GeoJSON using `tools/build_world_detail.py`; no attribution/license text required |
| Microsoft Visual C++ runtime | Native runtime DLLs | Yes, when selected by Nuitka | Microsoft redistributable runtime terms | Exact files audited from final Windows artifact |
| Inno Setup 7.1.0 engine/uninstaller | Installer packaging | Yes, in Setup/uninstaller | Inno Setup License (`licenses/Inno-Setup-7.1.0.txt`) | Bundled license permits use for any purpose, including commercial applications; upstream separately requests commercial users purchase a commercial license |
| Nuitka 4.2.1 | Compiler | No | AGPLv3 + Nuitka Runtime Library Exception | Build-time only; runtime exception explicitly permits generated proprietary target code |
| MSVC compiler/build tools | Native compiler | No | Microsoft build-tool terms | Build-time only |
| jsdom 26.1.0 | Automated browser tests | No | MIT | Declared in `tests/package.json`; `node_modules` is not shipped |
| SimConnect | Simulator interface | No Microsoft binary shipped | External Microsoft component | Simulator-installed `SimConnect_internal.dll` discovered at runtime |
| GSX Pro / Couatl Remote API | External optional service | No | External product/service | WingTouch only connects to locally installed service |
| SimBrief / Navigraph service | External optional latest-OFP service and OFP-hosted briefing images | No | External product/service | Network integration only; remote chart images are not bundled or mirrored |
| AviationWeather.gov Data API | External data service | No | External U.S. government service | Network integration only |
| FAA d-TPP | Charts terminal-procedure source | No | External official FAA data source | XML metadata and selected PDFs fetched on demand; short-lived RAM cache only |
| GitHub Releases API | WingTouch update channel | No | External public GitHub service | Public release metadata/downloads only; release-builder token is not shipped |