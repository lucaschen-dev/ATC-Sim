# v1.0.14 · Build 48 — Taoyuan detail, source curves and aircraft scaling

**Build:** 48  
**Version:** 1.0.14  
**Record:** Retrospective release notes

## Changes

- Restore 49 Taoyuan main guidance paths previously misclassified as parking detail, and reveal stand guidance/numbers earlier.
- Review 37 nonpaved faces against the official ADC; remove false grass generated from annotation holes and recover real regions split by dashed lines.
- Fill two source-proven Taoyuan pavement omissions at the N cargo apron and S4/Q2, preserving protected islands and landside spaces.
- Repair the source-proven Macau A10-B4 paired-boundary pavement slit.
- Correct Lhasa cross-page registration, false S bends and confirmed pavement seams; retain true source turns.
- Limit screen ink width and smooth only reviewed curves within their original printed-ink envelope.
- Scale ground aircraft by actual length/wingspan and map scale; adapt hit testing and tag clearance while preserving text size.
- Migrate compatible Lhasa saved-route references without silently replanning aircraft.

## Recorded validation

Recorded checks include 19 airports, 72 stable native views/144 images; 106 aircraft geometry checks, 19 pointer-state checks and 1,398 Lhasa save-compatibility checks. Installation verified the build/resources and preserved all 53 original user-data files.

## Scope and limitations

The final actual window confirmed aircraft scaling and the Lhasa save. Continuous drag/FPS acceptance remained unverified because the computer-use tool rejected the gesture. Unreviewed source quantization and some unverified surface regions remain; this is not a full real-airport survey.

## Record basis

- `Models/ReleaseHistory.swift`
- `Documentation/Ground48/Report.md`
- `Documentation/Ground48/final-visual-review.md`
- `Documentation/Ground48/rctp-source-and-render-review.md`
- `Documentation/GroundAircraftScale48/Report.md`

These identifiers refer to retained private development records; the source code and reports are not distributed in this repository. Older features describe that build and may have been changed or removed later. See the [current player guide](../docs/HOW_TO_PLAY.md).

This history was published retrospectively on 2026-11-09. The GitHub publication time is not the original development/release date. Tags identify documentation snapshots, not historical game source trees. No application binary is attached.
