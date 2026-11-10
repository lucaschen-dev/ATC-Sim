# ATC Sim v1.1 — Build 49

Duty, review and display update. Release date: 2026-11-10.

## Play modes

- Free duty, 15-minute shifts, a five-aircraft completion challenge and 20-minute traffic waves.
- Demand waves continue to respect airport capacity, occupancy, separation and weather admission rules. CSV scheduling remains separate.
- Duty review uses recorded traffic and radio events, with a time selector, 20× playback, event filters and the existing service ratings.
- Review history is saved locally with the duty. Trajectories are sampled every five seconds and bounded to 20 minutes; radio history is bounded to 1,200 events. Review is not an editable rewind.

## Ground and radar

- Physical-scale ground detail: trunk taxi identifiers and the selected route remain useful at an overview; parking linework, stand numbers and fine junction labels reveal closer in.
- Consistent, clipped terminal surface finish and construction hatching. Existing source footprints, genuine landside voids, straight lines and source curves are retained.
- Reviewed bundled airport geometry takes precedence over obsolete generated imports, while retaining the previous package identity and save location. User-authored packages are not overwritten.
- Aligned GND/APP/ACC workspace proportions, regular typography, stable clearance controls and individual CLR/LOC/GS state cues.
- Full versus limited radar tags reflect ownership and selection. Repeated current/cleared altitude is omitted from an unselected level-flight tag. Neighbor traffic stays subordinate.
- Weather and terrain brightness are independently adjustable. Coordination-only fuel areas no longer clutter the default map. Map annotations remain directly beside/above their objects without leader lines.
- When a constraint stack cannot fit above a fix, its identifier can still be shown without relocating the fix. Zooming reveals additional detail where space permits.

## Safety and responsiveness

- Air separation prediction intersects lateral and vertical conflict intervals over the lookahead, rather than checking only one horizontal closest-approach instant.
- Handles parallel vertical convergence, safe level-offs, threshold tangencies and conflicts that occur before horizontal CPA. Selected-pair projections include estimated time to loss of separation.
- New random warm starts and later traffic admissions are screened for imminent conflicts with the same lookahead, rather than accepting current spacing alone. Unsafe candidates wait for a later opportunity.
- The initial ground training summary appears once when setup replaces the default traffic plan.
- Attention animation is separated from stable radar routes, labels and targets. Expanding waves paint below text.
- Cached static ground structure counts avoid repeated command scans during view updates.
- Simulation pulses use monotonic elapsed time and discard long background/sleep gaps, avoiding a burst of overdue admissions on wake.

## Validation and scope

Release builds, duty/conflict checks, ILS and emergency regressions, save-compatibility checks, bilingual native rendering, all-airport ground/radar display screening and native-window interaction were used for this update. Exact validation results and performance limits are recorded in [the v1.1 design/validation note](../docs/V1_1_DESIGN.md).

The original black/white interface, square frames, yellow ground aircraft and green crosshair are retained. No art or gameplay source from the studied products is bundled. This is an entertainment simulation with historical source data and training sectors, not an operational ATC system.

**Documentation-only release:** no app, installer, private source, charts/PDFs or player saves are attached. GitHub's automatic source archives contain this public documentation repository only.

[Full player guide](../docs/HOW_TO_PLAY.md)
