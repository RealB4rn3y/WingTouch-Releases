# WingTouch — Release License BOM

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
| MapLibre GL JS 5.18.0 | Browser vector-map renderer | Runtime network dependency; not bundled as a local JS package | BSD-3-Clause (`licenses/MapLibre-GL-JS-NOTICE.txt`) | Loaded from a pinned unpkg URL; the notice points to the exact v5.18.0 upstream BSD-3-Clause license |
| OpenFreeMap public service | Default replaceable online vector style/tile provider | No provider software bundled | External service terms (`licenses/OpenFreeMap-Service-NOTICE.txt`) | Styles/tiles fetched on demand; provider project page states commercial use is allowed and attribution required; current public service has no SLA guarantee |
| OpenMapTiles schema | Schema used by the default provider for vector layers such as `aeroway` | No OpenMapTiles build stack/database bundled | BSD + CC BY schema terms; attribution required (`licenses/OpenMapTiles-NOTICE.txt`) | Provider-supplied source attribution credits OpenMapTiles |
| OpenStreetMap data | Underlying geography in the default vector basemap | No local OSM database bundled | ODbL 1.0 (`licenses/OpenStreetMap-ODbL-NOTICE.txt`) | Interactive-map attribution remains visible and links to OpenStreetMap copyright/license information |
| Microsoft Visual C++ runtime | Native runtime DLLs | Yes, when selected by Nuitka | Microsoft redistributable runtime terms | Exact files audited from final Windows artifact |
| Inno Setup 7.1.0 engine/uninstaller | Installer packaging | Yes, in Setup/uninstaller | Inno Setup License (`licenses/Inno-Setup-7.1.0.txt`) | Bundled license permits use for any purpose, including commercial applications; upstream separately requests commercial users purchase a commercial license |
| Nuitka 4.2.1 | Compiler | No | AGPLv3 + Nuitka Runtime Library Exception | Build-time only; runtime exception explicitly permits generated proprietary target code |
| MSVC compiler/build tools | Native compiler | No | Microsoft build-tool terms | Build-time only |
| jsdom 26.1.0 | Automated browser tests | No | MIT | Declared in `tests/package.json`; `node_modules` is not shipped |
| SimConnect | Simulator interface | No Microsoft binary shipped | External Microsoft component | Simulator-installed `SimConnect_internal.dll` discovered at runtime |
| GSX Pro / Couatl Remote API | External optional service | No | External product/service | WingTouch only connects to locally installed service |
| SimBrief / Navigraph service | Optional latest-OFP retrieval and OFP-hosted briefing data/images | No SimBrief/Navigraph software or navigation database bundled | External service/developer terms (`licenses/SimBrief-Navigraph-NOTICE.txt`) | The vector map does **not** plot SimBrief navlog waypoints or OFP route geometry. **Release action:** confirm any Developer Application registration/client-ID requirements for WingTouch’s documented latest-OFP use before publishing 0.3.5. |
| AviationWeather.gov Data API | External data service | No | External U.S. government service | Network integration only |
| FAA d-TPP | Charts terminal-procedure source | No | External official FAA data source | XML metadata and selected PDFs fetched on demand; short-lived RAM cache only |
| GitHub Releases API | WingTouch update channel | No | External public GitHub service | Public release metadata/downloads only; release-builder token is not shipped |
