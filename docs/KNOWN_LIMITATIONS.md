# Scope and known limitations

This document accompanies **v1.1, build 49**.

- ATC Sim is an entertainment simulation, not an operational ATC system or certified training device. It combines chart-derived data with simplified aircraft behavior and training rules.
- The 19 playable airport packages have different levels of operational coverage. Printed stand numbers, nearby-airport symbols and reference-only procedures must not be interpreted as complete executable support.
- Ground stand admissions use a reviewed subset. Aircraft size, occupancy, route feasibility and terminal/airline preference can exclude a stand. The game does not promise the entire real airport's stand capacity.
- Historical chart data is not maintained as a live AIP/NOTAM service. Weather and traffic are simulated; there is no live METAR, radar or flight-schedule feed.
- Terrain contours come from retained elevation grids. Display smoothing improves readability, not the underlying measured resolution. Training-sector boundaries and transfer rules are not published FIR boundaries or real unit agreements.
- Not every conventional turn, RF/conditional leg, nonprecision vertical profile or visual continuation is automatically supported. A reference path is not an automatic approach clearance. ILS is available only in supported airport/runway/context combinations.
- GND and the air simulation have separate scenario state. There is no fully continuous world automatically transferring the same aircraft across all three positions.
- The standalone DEL position and in-game airport editor are unavailable. Historical editor, PDF-analysis and dispatch features in old release notes are not current features. Voice output is not included.
- Roof panel finishes and construction hatching are presentation materials inside existing footprints, not surveyed architectural detail.
- Some source-chart quantization and unverified surface regions remain. The build-48 review covered 19 airports and focused repairs, not a complete real-airport survey. In particular, the Macau A10–B4 slit repair does not establish the correctness of every other dark area.
- Native rendering and save-compatibility checks passed within their recorded scope. Build 49 also received installed-window checks for ground zoom/pan, review playback and an APP ILS-to-tower flow. Continuous pointer/label dragging could not be completed reliably by the window-control tool, and live FPS was not measured. Static screenshots and offscreen measurements are not guarantees of frame rate or complete freedom from stutter.
- Older screenshots may show controls, symbols or color treatment that changed later. Each image is labeled with its captured build.

Use [bug reporting](BUG_REPORTING.md) for a reproducible problem. Public GitHub Releases are documentation records; there is no game application download attached.

The v1.1 ground audit screened 19 airports in 58 overview/terminal views, and radar annotation checks covered APP and ACC at all 19. That is not a corner-by-corner validation of every real airport feature. Recorded-duty playback is sampled history, not a full simulation replay. Conflict lookahead holds present ground-track motion and caps vertical motion at the cleared altitude; future turns can change the result.
