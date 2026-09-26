<div align="center">
  <img src="web/assets/wingtouch-logo.png" alt="WingTouch" width="720">
</div>

# WingTouch

**A local-first cockpit companion for Microsoft Flight Simulator.**

WingTouch turns a second screen, tablet, or browser into a flexible companion for your simulator setup. It combines a customizable Home dashboard, panel creation tools, live simulator telemetry, checklists, flight-planning helpers, weather, charts, GSX controls, notes, ATC utilities, and more in one consistent interface.

**Current release:** `0.3.1`  
**Platform:** Windows x64  
**Primary simulator target:** Microsoft Flight Simulator 2024  
**Status:** Early release / active development

> [!WARNING]
> **For flight simulation only. Not for real-world navigation or aircraft operation.**

---

## What WingTouch does

WingTouch runs locally on the simulator PC and serves its interface to a browser. That means the same workspace can be used on the desktop, an iPad, another tablet, or another device on the local network without requiring a separate companion app on the tablet.

### Highlights

- **Customizable Home dashboard** with built-in and user-created gadgets
- **Panel Creator** for touch-friendly cockpit panels and button boxes
- **Live telemetry and controls** through SimConnect
- **Channel Library** for MSFS, FlyByWire, custom telemetry/actions, and shareable custom channel folders
- **GSX Pro Controls** through the local Couatl Remote API
- **SimBrief basics** including OFP data, flight summary, route map, and a dedicated Runway Analysis performance page
- **Weather basics** with airport weather, METAR data, and SimBrief OFP weather/briefing charts
- **FAA Charts** with on-demand terminal procedure charts and a dedicated chart viewer
- **Normal and abnormal checklists**
- **ATC Basic** tools for radio/transponder workflows
- **Quick Notes** with keyboard and handwriting support
- **Dark and Light themes** with WingTouch wallpapers
- **Built-in update workflow** for supported release builds

---

## Local-first by design

WingTouch is designed around the simulator PC and the local network.

- The WingTouch web server runs on the simulator PC.
- Your workspace and user-created content are stored locally.
- A tablet can connect over the local network using the WingTouch URL/QR workflow.
- WingTouch does **not** add analytics, advertising, or usage tracking.
- External network access is only used when a feature requests an external service, such as SimBrief, AviationWeather.gov, FAA charts, or GitHub release/update data.

Some integrations are optional and may require their corresponding third-party product or service.

---

## Getting started

### Windows release

The normal end-user release is a standalone Windows x64 build.

1. Download the latest WingTouch release.
2. Install WingTouch.
3. Start `WingTouch.exe`.
4. Start Microsoft Flight Simulator.
5. Open WingTouch from the system tray.
6. Use **Open Tablet QR** or **Copy Tablet URL** to connect an iPad/tablet on the same local network.

End users do **not** need to install Python, pip, Node.js, Nuitka, or other development tools.

### Local network access

WingTouch uses TCP port `8765` by default. The installer can optionally create a Windows Firewall rule limited to the **Private** profile and the **local subnet**.

---

## Simulator support

WingTouch is primarily developed for **Microsoft Flight Simulator 2024**.

The simulator connection uses the SimConnect library installed with Microsoft Flight Simulator. WingTouch does not redistribute Microsoft's SimConnect DLL. For diagnostics and manual-path setup, the MSFS 2024 target ends in `MSFS2024\SimConnect_internal.dll`; the MSFS 2020 target ends in `MicrosoftFlightSimulator\SimConnect.dll`. WingTouch can auto-detect supported installations or use the path selected in Settings.

MSFS 2020 can be selected in the simulator settings for compatible SimConnect functionality, but the main development and testing target is MSFS 2024.

---

## Integrations

| Integration | Status | Purpose |
| --- | --- | --- |
| Microsoft Flight Simulator / SimConnect | Shipped | Simulator telemetry and controls |
| FlyByWire A32NX / A380X | Shipped | Telemetry/control catalog and WingTouch-authored checklist presets |
| GSX Pro | Shipped | Ground-service controls through the local Couatl Remote API |
| SimBrief | Shipped | Latest OFP data, flight summary, route map, and imported Runway Analysis performance data |
| AviationWeather.gov | Shipped | Current airport weather observations |
| FAA d-TPP | Shipped | On-demand terminal procedure charts |
| GitHub Releases | Shipped | WingTouch release/update metadata |
| Navigraph | Research | Future supported integration |
| VATSIM | Research | Future supported integration |
| SayIntentions.AI | Research | Future supported integration |
| ChartFox | Research | Future supported chart integration |

Third-party services remain subject to their own availability, terms, authentication requirements, and licenses.

---

## Panel Creator

WingTouch includes a visual Panel Creator for building custom simulator control surfaces.

Panels can contain buttons, annunciators, switches, rotary controls, values, text, frames, navigation controls, and other WingTouch components. Widgets can be connected to supported simulator channels and used as interactive touch controls.

User-created panels and Home Gadgets can be exported and shared. Creator attribution, panel metadata, and update/download URLs are preserved by the WingTouch panel format.

---

## Telemetry & Channel Library

The Channel Library is the bridge between simulator data and WingTouch widgets.

Supported channel types include simulator variables, events/actions, supported local variables/input events, and WingTouch-defined channels where available.

Users can also create their own channels and organize them into folders. Custom top-level folders can be exported as portable WingTouch channel packs and imported by other users without copying the built-in MSFS, FlyByWire, or GSX catalogs.

---

## Charts

WingTouch includes basic FAA chart support using official FAA d-TPP data.

Charts are fetched on demand and displayed inside the WingTouch chart viewer. WingTouch does not bundle or permanently mirror FAA chart sets.

> [!CAUTION]
> WingTouch charts are for **flight simulation only** and must not be used for real-world navigation.

---

## Roadmap

### Shipped

Home · Checklist · ATC Basic · Quick Notes · GSX Pro Controls Support · SimBrief Basics Support · Weather Basics + OFP Weather Charts · Charts Basics — FAA only · Panel Creation Tool · Enhanced Telemetry · Easy Update

### Research

SimBrief T.O. Performance Calculator · Navigraph Support · VATSIM Support · SayIntentions.AI · ChartFox · SimBrief Flight Plan Creation Tool

Research items are not promises or release commitments. They indicate areas being investigated for technically and legally supported integration.

---

## Privacy

WingTouch is designed without analytics or usage tracking.

Workspace data, panels, gadgets, notes, preferences, and other user-created project data stay in the local WingTouch data directory unless the user explicitly exports or shares them.

Optional integrations may send the information required by that feature to the relevant third-party service. For example, a SimBrief refresh uses the configured Pilot ID, weather requests contact AviationWeather.gov, and chart requests contact official FAA sources.

---

## License

WingTouch is **proprietary software**.

Copyright © 2026 B4rn3y. All rights reserved.

The WingTouch license grants a limited right to use WingTouch for **personal, non-commercial purposes**, and explicitly permits WingTouch to appear in **monetized or sponsored videos, livestreams, reviews, tutorials, screenshots and similar media content** without separate permission. This creator/media exception covers revenue such as ads, subscriptions, donations, sponsorships and platform payouts. Redistribution, resale, sublicensing, public distribution of modified builds, rebranding, bundling WingTouch into another commercial product/service, or other commercial exploitation of WingTouch itself still requires prior written permission unless mandatory law provides otherwise.

Users retain ownership of their own original content created with WingTouch, including their own panels, Home Gadgets, layouts, configurations, presets, notes, and other user-created project data.

The WingTouch name, logo, visual identity, and official branding are reserved.

Please read the complete terms before using or redistributing anything from this project:

- [`LICENSE.txt`](LICENSE.txt) — WingTouch Proprietary Software License
- [`EULA.txt`](EULA.txt) — End User License Agreement

Licensing and permission requests: **wingtouch@b4rn3y.org**

---

## Third-party components and notices

WingTouch uses or interacts with third-party software, data, APIs, and services. Those components remain subject to their own licenses and terms.

The public release repository keeps the human-readable release/legal documents with the project:

- [`THIRD-PARTY-NOTICES.md`](THIRD-PARTY-NOTICES.md) — third-party notices and source references
- [`LICENSE-BOM.md`](LICENSE-BOM.md) — release license/component bill of materials

The downloadable Windows distributions additionally carry the complete `licenses/` directory and the `catalog-sources/` provenance material required by the packaged build. The private source repository retains the corresponding generation/audit tooling.

Notable shipped/runtime components include CPython runtime components, OpenSSL/libffi where selected by the Windows build, `websockets`, and the MIT-licensed QR generator. Both SimBrief route-map views use the build-generated Natural Earth 1:50m public-domain land/lake/country-boundary layer when available. The lightweight 1:110m world asset remains bundled only as an offline/failure fallback if the generated detail asset is unavailable.

FlyByWire documentation/catalog snapshots retain their supplied GPLv3 provenance. WingTouch-authored A32NX/A380X checklist presets are not official FlyByWire checklists, and FlyByWire Simulations is not affiliated with or endorsing WingTouch.

WingTouch does not redistribute Microsoft Flight Simulator, SimConnect, GSX Pro, SimBrief/Navigraph software, AviationWeather.gov datasets, or FAA chart collections.

---

## Project status

WingTouch `0.3.1` is an early release and remains under active development.

The project has grown from a simple tablet control-panel idea into a broader simulator companion. The current focus is stability, touch usability, reliable simulator integration, safe third-party integrations, and a release process that keeps user data and licensing boundaries clear.

Bug reports and focused feedback are welcome.

---

## Credits

**WingTouch** is created by **B4rn3y**.

Third-party projects, documentation sources, services, and datasets are credited in [`THIRD-PARTY-NOTICES.md`](THIRD-PARTY-NOTICES.md) and the accompanying license files.

---

<div align="center">

**WingTouch · Your cockpit. Your way.**

</div>
