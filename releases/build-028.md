# Build 28 — Ground color and tile coverage

**Build:** 28  
**Version:** 0.1  
**Record:** Retrospective release notes

## Changes

- Prevented incomplete or undersized map tiles from replacing complete native-density content.
- Prepared source vectors and Boolean surface masks at airport load to reduce repeated work.
- Applied supported grass, pavement, building, construction and water categories consistently.
- Corrected reviewed Hong Kong and Urumqi surface seams without changing operational routes.

## Recorded validation

The recorded native harness covered 1,007 viewport states across 19 airports.

## Scope and limitations

Native rendering/readback measurements are not display FPS. Live continuous gesture verification remained incomplete.

## Record basis

- `Documentation/GroundPanSurfaceRepair20261101/REVIEW.md`

These identifiers refer to retained private development records; the source code and reports are not distributed in this repository. Older features describe that build and may have been changed or removed later. See the [current player guide](../docs/HOW_TO_PLAY.md).

This history was published retrospectively on 2026-11-09. The GitHub publication time is not the original development/release date. Tags identify documentation snapshots, not historical game source trees. No application binary is attached.
