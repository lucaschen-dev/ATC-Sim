# v1.0 · Build 34 — Version 1.0

**Build:** 34  
**Version:** 1.0  
**Record:** Retrospective release notes

## Changes

- Make pilot requests depend on the actual route, phase, restrictions, weather and current approval context.
- Prefer eligible reviewed contact stands for departures and arrivals, with occupancy, aircraft size and route feasibility taking priority.
- Prepare airport assets in the background and add a loading surface before opening a position.
- Add persistent English/Simplified Chinese UI, a mandatory ten-page first-run guide and consistent square controls.
- Turn an APP target green only after both LOC and GS capture; warning colors retain priority.
- Keep GND, APP and ACC as the selectable positions, withdraw DEL/editor entry points and add the in-app version timeline.

## Scope and limitations

Voice output was discussed but is not included. Positions remain separate saved scenarios rather than one continuous shared world.

## Record basis

- `Models/ReleaseHistory.swift`
- `Documentation/Build34Delivery.md`

These identifiers refer to retained private development records; the source code and reports are not distributed in this repository. Older features describe that build and may have been changed or removed later. See the [current player guide](../docs/HOW_TO_PLAY.md).

This history was published retrospectively on 2026-11-09. The GitHub publication time is not the original development/release date. Tags identify documentation snapshots, not historical game source trees. No application binary is attached.
