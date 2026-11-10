# v1.1 design study and validation

Version 1.1, build 49. Updated 2026-11-10.

This update studies established ATC games and simulators while retaining ATC Sim's black display, regular machine-style typography, square controls, yellow ground aircraft and green crosshair. It is not a port of another product. No third-party game artwork or gameplay source was copied into this release.

## Reference study

| Reference | Evidence examined | Lesson applied |
|---|---|---|
| [ATC Ground Point](https://store.steampowered.com/app/3239550/ATC_Ground_Point/) | Official screenshots and sampled gameplay trailer | Airport surfaces and parking detail should sit behind active aircraft and cleared routes. Ground detail now follows physical map scale, with a consistent clipped terminal finish. |
| [Endless ATC](https://store.steampowered.com/quickref/666610) | Official manual, developer guide and sampled gameplay trailer | Keep clearance controls in stable locations and make approach phases explicit. The inspector now shows separate CLR, LOC and GS states. |
| [Mini Airways](https://store.steampowered.com/app/2289650/Mini_Airways/) | Official screenshots and sampled launch trailer | Use consistent state feedback and bounded play sessions. Free, timed, completion-target and traffic-wave duties share the same operational controls. |
| [Radar Identified](https://store.steampowered.com/app/4534350/Radar_Identified/) | Official screenshots and sampled update trailer | Keep coordination and exit context separate from traffic geometry. Conflict projections show the selected pair and estimated time to loss of separation. |
| [openScope](https://github.com/openscope/openscope) | Public demo selection interaction and source review | Link one selected flight to its controls and relevant route; separate stable map work from transient attention effects. |
| [Vice](https://github.com/mmp/vice) | Official documentation and source review | Vary tag detail with ownership and selection; provide independent map/weather brightness controls. |
| [ATC-pie](https://wiki.flightgear.org/ATC-pie_user_guide) | Official guide and public source review | Keep straight segments, explicit source curves, surface materials and operational routing separate. Do not round every airport connection. |
| [BlueSky](https://github.com/TUDelft-CNS-ATM/bluesky) | Official repository/wiki and rendering-source review | Keep physical aircraft geometry and protection distances separate from readable screen-space labels. Validate predictions and rendering independently. |

Commercial footage was observed, not played hands-on. openScope's public demo was interacted with. Vice, ATC-pie and BlueSky source was read; those native applications were not run. This is not a comparative frame-rate benchmark.

## What changed

- Ground linework, stand numbers and junction identifiers reveal detail at progressively closer physical scales. Main taxi identifiers and relevant route context remain useful at an overview.
- Terminal panel finish and construction hatching are clipped to existing footprints. They are display materials, not new surveyed architectural detail. Genuine landside voids remain unfilled.
- Reviewed bundled airport assets supersede obsolete generated imports without changing the previous save location or overwriting user-authored packages.
- GND, APP and ACC share workspace proportions and aligned control sizes. Selected tracks expose useful detail; unselected level tracks omit duplicate current/cleared altitude, and external tracks remain subordinate.
- Terrain and precipitation brightness can be adjusted independently. Map annotations have no leader lines; a fix name can remain visible when its full constraint stack will not fit above it.
- Four duty modes add clear session boundaries. Review displays actual recorded plots and radio events, sampled every five seconds for up to 20 minutes. It cannot rewind and change the simulation.
- Conflict prediction intersects the time intervals of unsafe lateral and vertical separation, including parallel vertical convergence and level-offs. Random warm starts and later admissions also use the imminent-conflict screen. Present-track extrapolation does not predict future route turns.
- Radar attention effects animate separately from stable plotting. Static ground command counts are retained rather than rescanned on each update. Long sleep/background gaps are discarded by the simulation clock.

The existing source-based airport geometry, surface-union renderer and tile cache were retained. This release does not claim a fresh survey or complete geometry redraw of all 19 airports.

## Validation

The release was checked with production SwiftUI/AppKit rendering and operational regression fixtures, not a replacement web mockup.

| Check | Scope / result |
|---|---|
| Release build | Native macOS build; installed bundle signing and App Sandbox checked; no bundled PDF files. |
| Duty and conflict checks | 21 checks passed: session boundaries, bounded demand, trajectory/event retention, save round trips, clock gaps, analytic conflict cases and five random warm-start seeds. A parallel vertical-convergence regression fails with the previous predictor and passes with the interval predictor. |
| ILS regressions | 94 checks passed. |
| Pilot/emergency regressions | 69 checks passed. |
| Workstation/native save checks | 22 bilingual native captures plus retained-workspace and save-compatibility checks. |
| Ground screening | 19 airports, 58 overview/terminal views and first/settled render pairs; all contact sheets inspected, with additional close inspection of Guangzhou, Lhasa and Taoyuan. |
| Radar annotation checks | APP and ACC at all 19 airports: 12,833 checks passed. Checks cover annotation placement, units, runway labels, route duplication and leader-line absence. |
| Actual installed-window checks | Ground selection/pushback, follow/zoom and scroll-pan; duty review time selection/playback; APP altitude/IAS clearances, layer controls, LOC/GS capture and the tower acceptance/transfer sequence. |

These are bounded checks. They do not establish that every real airport feature, every source restriction, or every high-density scenario is correct. Automated continuous pointer/label dragging could not be completed reliably with the available window-control tool. Live compositor frame rate was not measured.

### Performance measurements

The same production ground canvas was measured through 24 changing pan/zoom viewports per airport, at 1280 × 800 logical points and 2× backing scale. The following values are warm layout/update p95 in milliseconds:

| Airport | Before | v1.1 |
|---|---:|---:|
| Guangzhou ZGGG | 6.45 | 6.69 |
| Lhasa ZULS | 4.43 | 3.61 |
| Shanghai Pudong ZSPD | 4.27 | 4.17 |

This is an offscreen host measurement. Bitmap readback was measured separately; neither number is an FPS result. Guangzhou's measured layout p95 did not improve, and cold source preparation remains comparatively expensive there. The update reduces specific redundant work; it does not claim that all stutter has been eliminated.

See [known limitations](KNOWN_LIMITATIONS.md), [how to play](HOW_TO_PLAY.md) and [build 49 release notes](../releases/build-049.md).
