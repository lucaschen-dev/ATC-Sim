# ATC Sim

**A native macOS air traffic control game.** Manage airport surface movement, sequence arrivals and departures, and coordinate aircraft through an area-control sector.

[How to play](docs/HOW_TO_PLAY.md) · [Release history](CHANGELOG.md) · [GitHub Releases](https://github.com/lucaschen-dev/ATC-Sim/releases) · [Traffic schedules](docs/TRAFFIC_SCHEDULES.md) · [Report a bug](docs/BUG_REPORTING.md)

**Current documented version: v1.1.6 · Build 55.** The current local build targets **macOS 26 or later on Apple silicon**. The interface supports English and Simplified Chinese.

This repository is the public player guide and development release archive. It contains documentation, game screenshots and fictional CSV training schedules. **The game application, installers, private source code, player saves and source-chart PDFs are not hosted here.** No public download is announced in this repository. GitHub's automatically generated “Source code” archives contain these documentation files only.

## The game

ATC Sim focuses on the controller's working display: dark backgrounds, compact monospaced labels, square controls, chart-derived airport geometry and a green crosshair cursor. Aircraft follow clearances and take time to turn, climb, slow down and taxi.

| Position | Your job |
|---|---|
| **GND — Ground** | Approve pushback, plan taxi routes, resolve surface conflicts, manage runway crossings and departure clearances, and guide arrivals to stands. |
| **APP — Approach** | Sequence arrivals and departures with heading, altitude and IAS clearances; establish supported approaches and complete tower/area handoffs. |
| **ACC — Area** | Accept arrivals, departures and overflights, maintain spacing, meet exit conditions and coordinate transfer to the next unit. |

Choose free duty, a 15-minute shift, a five-aircraft completion challenge, or a 20-minute traffic-wave shift. Review recorded traffic and radio events afterward. Weather and traffic are adjustable. Endless traffic arrives gradually according to demand, airport workload and weather. CSV mode lets you supply a reviewed schedule. Contextual pilot calls, emergency coordination, precipitation echoes, terrain warnings and a satisfaction score add decisions beyond routine vectoring. Optional cloud radio speech uses the player’s own ElevenLabs API key, Chinese/English male-voice auditions, volume and rate controls. It stays silent until configured and enabled.

The airport editor and standalone clearance-delivery position are currently unavailable. They appear in older release notes as historical features.

## Actual game screenshots

These images show ATC Sim's own native game display. They are not concept art or screenshots from the reference games. See [screenshot provenance](docs/SCREENSHOTS.md).

### Airport selection and approach radar

![ATC Sim v1.1.1 fictional airport cards](assets/v1.1.1-airport-cards.png)

![ATC Sim v1.1.1 weather and aircraft labels](assets/v1.1.1-approach-weather.png)

*Fictional airport names, monochrome painted-letter cards, blue callsigns, green flight values and continuous precipitation contours. The home screen retains its looping approach-radar video.*

![ATC Sim v1.1.1 ground display](assets/v1.1.1-ground.png)

*Darker pavement, subordinate parking guidance, yellow aircraft and type-relative airframe sizing. Different engine/airframe families use separate silhouettes.*

Historical v1.1 ground and duty-review frames remain in [screenshot provenance](docs/SCREENSHOTS.md).

## Start playing

1. Open your installed copy of **ATC Sim**. Complete the first-run illustrated tutorial.
2. In **Settings**, choose **English** if needed.
3. Choose **Start Game**, an airport card, then **GND**, **APP** or **ACC**.
4. Start with light endless traffic and benign weather. You can adjust cloud base, visibility, wind, gusts, QNH and precipitation.
5. Select an aircraft, read its request and issue clearances from the right-hand panel. A route preview or background procedure does not issue a clearance.
6. Pause whenever you need time to plan. Read the [full guide](docs/HOW_TO_PLAY.md) for complete GND, APP and ACC workflows, ILS capture, transfers and emergencies.

## Airport library

The current bundled library contains **20 playable airport packages**, displayed under fictional names. Existing four-letter codes identify the same scenarios, routes, CSV records and saves. Each airport has its own supported ground and air data. Available procedures and operational stands vary by airport.

| ICAO | Airport | ICAO | Airport |
|---|---|---|---|
| ZGGG | Aster Bay | ZULS | Kora Highlands |
| ZSSS | Valmere City | ZBAA | Nordhaven |
| ZUUU | Monteluce | VMMC | Porto Vela |
| ZSCN | Harrowfield | ZHHH | Bellarive |
| ZUCK | Sierra Alta | ZSHC | Kiyora Lake |
| ZYHB | Frostvik | ZGHA | Solterra |
| ZHCC | Dunewick | ZSJN | Redwillow |
| ZSFZ | Aokaze Coast | VHHH | Meridian Isles |
| RCTP | Akari Coast | ZSPD | Luminara |
| ZWWW | Qamar Ridge | KLAX | Pacific Bluffs |

## Progress and controls

Sessions are saved locally. GND and the air simulation use their own scenario state; this is not a shared continuous world in which the same aircraft automatically moves through all three positions. Use the same airport/position and the available resume action to continue a saved duty.

| Action | Control |
|---|---|
| Pause/resume | **⌘P** |
| Save | **⌘S** |
| Save and return home | **⌘⇧H** |
| Tutorial/manual | **⌘/** |
| Toggle fullscreen | **⌃⌘F** |
| Pan / zoom | Drag blank map space / scroll or pinch |
| Move a tag | Drag the aircraft label |

## Releases

There is one [GitHub Release](https://github.com/lucaschen-dev/ATC-Sim/releases) per documented build, with an English change list and scope notes. Build-number tags, such as `build-048`, identify documentation snapshots; they do not contain a historical application or its private source tree. Earlier development builds are marked as prereleases.

Builds 5, 11, 12 and 20 are omitted because separate records could not be established. See the [complete index](CHANGELOG.md).

[Version 1.1.6 / build 55](releases/build-055.md) adds Pacific Bluffs (KLAX), improves stand guidance and pushback, and refines Mandarin radio and the settings cursor. [Version 1.1.5 / build 54](releases/build-054.md) adds automatic GitHub attachments and restores voice selection across launches. [Version 1.1.4 / build 53](releases/build-053.md) opens a prefilled GitHub bug form and prepares a diagnostic ZIP. [Version 1.1.3 / build 52](releases/build-052.md) improves radio settings, request pacing, sound effects and ground display. [Version 1.1.2 / build 51](releases/build-051.md) adds immediate interruption and push-to-talk sound effects for radio speech. [Version 1.1.1 / build 50](releases/build-050.md) adds fictional display names, painted-letter cards, colored radar tags and smoother weather contours. [Version 1.1 / build 49](releases/build-049.md) introduced duty modes and recorded review, refines ground detail and workstation layout, fixes stale imported geometry taking precedence over reviewed airport updates, and checks complete lateral/vertical conflict intervals. [Design study and implementation](docs/V1_1_DESIGN.md) explains the reference research and the limits of the update.

## Feedback and simulation scope

Use **Report a Bug** in the game, enter the problem, and choose **Report on GitHub**. The game opens the prefilled GitHub form in its own window and automatically attaches the ZIP. Sign in if prompted, review the draft, then select **Create**. See [bug-reporting steps](docs/BUG_REPORTING.md).

ATC Sim is an entertainment simulation. Chart-derived geometry and real elevation data are combined with simplified flight models, fictional training sectors and simulated traffic/weather. Data is not maintained as a live AIP, NOTAM, METAR, radar feed or operational ATC service. See [known limitations](docs/KNOWN_LIMITATIONS.md).
