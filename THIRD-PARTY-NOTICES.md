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

**WingTouch checklist presets:** the bundled A32NX/A380X simulation presets are WingTouch-authored data informed by public FlyByWire procedure/API references. They are not represented as official FlyByWire checklists. FlyByWire Simulations is not affiliated with or endorsing WingTouch. Provenance is recorded in `catalog-sources/checklist-presets-source.json`.

## WingTouch 0.3.1 SimBrief OFP briefing-image review

The current latest-OFP response can contain an `images` section with a SimBrief-hosted directory plus named map links (for example Route, SIGWX, upper-air wind and Vertical Profile images). WingTouch normalizes only HTTPS URLs hosted on `simbrief.com` or its subdomains and displays those remote images directly on the Weather page. It does not guess filenames, scrape SimBrief pages, proxy/mirror the images, bypass authentication, or add a new runtime package. Historical notes below describing weather charts as unavailable document the earlier project state and are superseded by this current 0.3.1 integration.

Provider references reviewed for this integration: SimBrief System Changelog (`xml.fetcher.php` introduced in 2018.25; JSON support added in 2020.57) at https://www.simbrief.com/home/?page=changelog and SimBrief Developer Support at https://www.simbrief.com/home/?page=support .

## WingTouch 0.3.1 external-source and updater review

Charts adds no new runtime package, font, map engine or bundled third-party chart asset. WingTouch fetches the official FAA d-TPP XML metafile and selected PDFs on demand and keeps only short-lived in-memory caches.

The GitHub updater uses the public GitHub Releases REST API and release asset URLs. End users do not need a GitHub account or token. Update checks are cached server-side, installer downloads are accepted only after the WingTouch manifest and SHA-256 match, and no analytics or usage reporting are added. Cross-repository publishing is a release-builder action and uses a narrowly scoped secret token that is never shipped in WingTouch.

Source references and the reviewed access boundary are recorded in `catalog-sources/charts-provider-sources.json`.

## WingTouch 0.3.0 dependency/license audit

The 0.3.0 RC adds no new runtime dependency, font, map engine, tracking library or redistributed third-party asset. The audit checked Python/runtime dependencies, JavaScript/test dependencies, vendored source, licenses, catalog provenance, assets and external APIs/SDK references.

- `websockets` 16.0 remains BSD 3-Clause and its license text is bundled in both source/release license locations.
- Kazuhiko Arase's QR Code Generator remains MIT licensed and retains its source header plus bundled MIT text.
- Natural Earth states its raster/vector map data are public domain; WingTouch keeps only the simplified local geometry used by Route Map.
- FlyByWire source/documentation snapshots retain the supplied GPLv3 notice/source provenance.
- `jsdom` 26.1.0 is test-only and is not shipped as `node_modules`.
- Nuitka 4.2.1 is pinned as a build-time compiler. Upstream 4.2.1 uses AGPLv3 with the Nuitka Runtime Library Exception; the exception explicitly permits generated target code, including proprietary programs, to be conveyed under other terms. Nuitka itself is not copied into the WingTouch source release as a dependency package.
- Inno Setup 7.1.0 remains the installer builder/engine. Its bundled license permits use for any purpose, including commercial applications. Upstream separately requests that commercial users purchase a commercial license. End users merely running a generated installer do not need Inno Setup installed.
- No Microsoft SimConnect DLL is bundled. WingTouch does not redistribute GSX Pro code, artwork, binaries or vendor-manual text, and no GSX software license is assigned by WingTouch. SimBrief/Navigraph and AviationWeather.gov remain network/service integrations.

Final native-distribution auditing is still required after producing the actual Windows Nuitka/installer artifacts because CPython/Nuitka can select native runtime DLLs based on the build environment. That artifact audit is separate from this clean source-tree RC package.

## WingTouch 0.2.13 feature/licensing review — targeted UI/UX refinement

The 0.2.13 UI/UX refinement adds no new runtime library, font, map engine, image asset or redistributed third-party component. Weather airport autocomplete reuses the already documented AviationWeather.gov data service through its official `stations.cache.json.gz` compressed station cache, fetched by the local backend and retained only as a short-lived in-memory cache. Quick Notes remains browser-native Canvas/Pointer Events/local storage, and SimBrief/Route Map changes reuse existing WingTouch-owned UI/SVG components.

## WingTouch 0.2.13 feature/licensing review — earlier pre-release polish

The 0.2.13 map controls reuse WingTouch's existing SVG/Natural Earth route-map data, Quick Notes changes use browser-native Canvas/Pointer Events/local storage, and the custom-wallpaper readability treatment is WingTouch CSS. No new runtime library, third-party map engine, font, image asset or redistributed component was introduced. SimBrief/Navigraph weather-chart access remains intentionally unimplemented because no supported stable chart-image API/deep-link contract was identified for the existing latest-OFP integration; WingTouch does not scrape private pages or bypass authentication/subscription controls.

Release preparation: WingTouch itself is proprietary under `LICENSE.txt` / `EULA.txt`. Retain all upstream notices and the bundled catalog source material referenced above. The Windows distribution does not include Microsoft SimConnect binaries; it discovers the user's simulator-installed `SimConnect_internal.dll`. Catalog presence does not certify aircraft compatibility.

The Windows x64 build uses Nuitka 4.2.1 as a **build-time compiler only**. Nuitka itself is not distributed as an end-user dependency; its Runtime Library Exception permits proprietary target code generated by the compilation process. Build reference: https://nuitka.net/doc/download.html and runtime exception: https://github.com/Nuitka/Nuitka/blob/develop/LICENSE-RUNTIME.txt .

References: https://opensource.org/license/mit and
https://www.gnu.org/licenses/gpl-3.0.html .

## WingTouch 0.2.0 owned/derived content

The ATC Helper wording in WingTouch 0.2.0 is original WingTouch quick-reference text using standard aviation terminology. The Light Mode WingTouch logo/icon variants are derived from WingTouch-owned artwork already bundled with the project. No new third-party runtime library or external asset was introduced for these features.


## WingTouch 0.2.1 external-service addition

SimBrief support uses the public latest-OFP service as an optional external integration. WingTouch sends the configured Pilot ID only when an OFP import/refresh is requested; it does not bundle SimBrief code, branding, flight-plan data or documentation prose. The schematic route map and SimBrief-page UI are WingTouch-owned presentation code.
## WingTouch 0.2.2 map-data addition

This section records the original 0.2.2 map-data addition. In current 0.3.1 builds, **both** the compact/Home route overview and the full Route Map use the locally generated Natural Earth 1:50m land/lake/Admin 0 boundary layer when `web/world-detail.js` is available; the simplified 1:110m asset is retained only as an offline/failure fallback. The 1:50m asset is generated during the release build from pinned Natural Earth v5.1.2 GeoJSON sources. Natural Earth publishes its raster and vector map data in the public domain and does not require attribution. WingTouch pre-projects the geometry into `web/world-detail.js` / `web/world-110m.js`; no runtime map library, online tile service, or proprietary map artwork is bundled. The aircraft symbol and route rendering are WingTouch-owned UI code.

## WingTouch 0.2.4 weather-data addition

Current airport observations use the external AviationWeather.gov Data API through the local WingTouch backend. WingTouch does not bundle AviationWeather.gov software or mirror its dataset; normalized observations are cached for five minutes to avoid repeated requests from multiple Weather/Home views. The official station cache used for autocomplete is cached in memory for 24 hours and is not redistributed with WingTouch. SimBrief OFP METAR text remains a planning snapshot and is labelled separately from current observations.

No stable supported weather-chart URL field was verified in the latest-OFP payload used by WingTouch 0.2.4, so the release does not construct guessed SimBrief map URLs or scrape SimBrief pages.


## WingTouch 0.2.12 installer tooling

WingTouch 0.2.12 uses Inno Setup 7.1.0 to produce the Windows installer. The installer and
uninstaller contain Inno Setup engine code under the Inno Setup License, retained in
`licenses/Inno-Setup-7.1.0.txt`. Inno Setup is not required on end-user machines.

The installer-managed build stores user workspace data and logs under `%LOCALAPPDATA%\WingTouch`
rather than under `Program Files`. The portable ZIP remains available as a separate fallback and
continues to keep its `data/` directory beside the executable.

The installer firewall task is optional and limited to the WingTouch executable, TCP port 8765,
the Windows **Private** firewall profile, and `LocalSubnet` remote addresses. It does not create a
Public-profile or Internet-wide inbound rule.
