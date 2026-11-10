# Build 16 — Asynchronous map preparation and Quit

**Build:** 16  
**Version:** 0.1  
**Record:** Retrospective release notes

## Changes

- Moved high-resolution ground preparation off the interaction path when the cache is not ready.
- Added Quit Game to the main menu.
- Preserved the active session while updating the installed game.

## Recorded validation

Recorded cache-entry checks covered 24 large pan/zoom cache misses with no foreground high-resolution generation.

## Scope and limitations

Cache-entry timing is not whole-game FPS or a guarantee of smoothness on every Mac.

## Record basis

- `Documentation/GroundRenderPerformanceVerification.md`
- `Documentation/GroundPerformanceReleaseVerification.json`
- `git:1a298661`
- `git:f9cac331`

These identifiers refer to retained private development records; the source code and reports are not distributed in this repository. Older features describe that build and may have been changed or removed later. See the [current player guide](../docs/HOW_TO_PLAY.md).

This history was published retrospectively on 2026-11-09. The GitHub publication time is not the original development/release date. Tags identify documentation snapshots, not historical game source trees. No application binary is attached.
