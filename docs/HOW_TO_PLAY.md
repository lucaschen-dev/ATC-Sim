# How to play ATC Sim

This guide describes **v1.1.3, build 52**. Earlier release notes may mention removed features. The selectable positions are **GND**, **APP** and **ACC**. Choose English in Settings; the language of a crew's radio messages may also depend on the flight's radio-language setting.

## 1. Start a duty

1. Open the game and finish the illustrated first-run tutorial. Use **Previous/Next** or the left/right arrow keys. **Finish** appears on the last page. You can reopen the tutorial later with **⌘/**.
2. Choose **Start Game** and select an airport card by its fictional display name or four-letter code. Codes and CSV/save identifiers retain their existing meaning. The card expands into the loading screen; the home menu keeps its looping radar video.
3. Select one position. You control one position for that duty; return home to choose another.
4. Set weather. Presets provide a starting point; cloud base, visibility, wind direction/speed, gusts, QNH and precipitation can be adjusted.
5. Choose **Endless** traffic or import a **CSV schedule**. Start with the light preset. The requested aircraft-per-minute rate is demand, not a promise to admit every flight immediately.
6. Choose a duty mode (described below), then start control and wait for the loading screen to finish. To continue a duty, use the available resume/continue action rather than starting a replacement session.

Bad weather, occupied stands, runway roles, separation and in-session capacity can delay admissions. Smaller airports have lower configured workloads. Traffic should build gradually; the map is not supposed to fill to its capacity at startup.

### Duty modes and review

| Mode | End condition | Traffic |
|---|---|---|
| Free duty | End it yourself | Your selected airport/weather demand |
| 15-minute shift | 15 simulated minutes | Your selected demand |
| Completion challenge | Five handled aircraft | No time limit |
| Traffic waves | 20 simulated minutes | Alternating demand, still subject to capacity and weather |

A timed shift ends by pausing the scenario; it does not wait for every aircraft already on the display to finish. Simulation time acceleration also accelerates the shift timer. CSV flights retain their scheduled admission logic; traffic-wave mode is unavailable for CSV traffic.

Open **… → Duty review** during play or **End duty** to finish. The review shows the existing safety, communication and coordination ratings, recorded traffic and a radio timeline. Select a time with the slider, press play for 20× playback, and filter radio events by ATC or Crew. This is a sampled record of the duty: five-second traffic samples, at most 20 minutes of trajectories and 1,200 radio events. It is not a rewindable simulation checkpoint; commands cannot be issued into the replay. A new attempt retains the traffic seed, but is not a guarantee that every later action or random event will be identical.

## 2. Read the display

Click an aircraft or its tag to open its controls. Read both the tag and the right-hand panel before issuing an instruction.

| Label | Meaning |
|---|---|
| Callsign, for example `CPA4312` | The flight's radio identity. It is not the transponder code. |
| `SQ` plus four digits | The octal transponder code. Emergency codes have specific meanings. |
| Actual altitude / `ALT` | Where the aircraft is now. |
| Cleared altitude / `CFL` | The altitude the controller has assigned. |
| `IAS` | Indicated airspeed; this is the speed-clearance input, in knots. |
| `GS` or `G` on a tag | Groundspeed. It changes with wind and altitude and need not equal IAS. |
| `HDG` / `°M` | Magnetic heading. |
| `LOC` | Localizer lateral tracking. |
| `GS` in the ILS status section | Glideslope capture, not groundspeed. Read the surrounding context. |

Altitude uses the scenario's displayed unit. Meridian Isles (`VHHH`), Porto Vela (`VMMC`) and Akari Coast (`RCTP`) use **ft**; the other bundled scenarios generally use **m**. Always check the unit beside a control. Weather wind direction uses its labeled true-direction convention; heading commands use magnetic heading.

Aircraft respond over time. Entering a number is not enough: commit it using the field's **SET/Enter** action, read the response and watch the actual value approach the cleared one. Published limits or performance constraints may reject a command or govern the effective target. A change in GS alone is not evidence that an IAS instruction was ignored.

### Map and labels

Owned normal callsigns use muted **blue**, flight values **green**, and neighboring/unowned traffic **violet**. Selection uses **gold**; conflict and emergency colors take priority. A captured LOC and GS still gives the aircraft its green approach indication. Ground aircraft remain yellow, with blue callsigns and neutral speed text.

Precipitation uses six continuous levels from green through ochre/orange to red. Echoes move and evolve with simulated weather; ordinary cloud and fog alone do not create rain returns. The contour shapes are reused across map pans and projected at the new zoom scale. WX brightness changes presentation only.


- Drag empty map space to pan; scroll/pinch or use the map zoom controls to change scale.
- Drag an aircraft's tag to move it away from map text. **TAGS** restores automatic layout.
- Use **Aircraft**, **Stand**, **Whole airport**, **Near field** or equivalent view controls when provided.
- The green crosshair marks the pointer position. Native file-selection dialogs may use the operating system cursor.
- Ground aircraft scale with aircraft length/wingspan and map zoom. At an overview, a common readability scale still preserves relative type sizes: a widebody is larger than a small jet. Twin-engine, four-engine, regional, business and turboprop families use distinct simplified silhouettes. Their labels remain at a readable fixed font size.
- In **Layers**, adjust **TERRAIN** and **WX** brightness independently. This affects appearance, not weather restrictions or terrain safety checks.
- Neighboring aircraft can use shorter tags; selecting a target exposes its full context.
- Background fix, runway and airspace annotations are map information. They do not issue instructions.

### Radio speech

Cloud speech is **off by default** and requires a personal **ElevenLabs API key**. Open **Settings → Radio speech**, or the in-duty speaker panel.

1. Paste your key into the concealed field and choose **Save**. The key is stored in this Mac’s Keychain, never in a save, preferences export or feedback ZIP. **Remove** deletes it.
2. Choose **Load male voices**, then choose a voice for Chinese and English. Use native-language voices for the best accent. A manual Voice ID field is available if your key cannot list voices.
3. Audition each language. An **Emergency audition** lets you compare urgent delivery. Turn on **Radio speech** at the top of the panel. The switch keeps your preference across restarts, setup changes and temporary service errors.
4. Adjust **Volume**, **Rate** and **Contextual urgency**. The initial rate is 1.15×. Voice choice and delivery remain subjective; the game does not guarantee actor-quality pronunciation.

The default speech model is **v4 Turbo (low latency)**. Choose **Eleven v3** in the model menu for its delivery style. Playback speed supports up to 2×. Radio text is sent to that service and billed to the player’s account; it is not microphone input or voice-command recognition. No game audio is generated without configuration. Read [provider pricing](https://elevenlabs.io/pricing/api) and [speech API documentation](https://elevenlabs.io/docs/api-reference/text-to-speech/convert).

Chinese callsigns, headings, speeds, runways and frequencies use explicit radio digit readings, including 洞 / 幺 / 两 / 拐. Heights with units use quantities. Actual transmission language follows its radio text, independently of the interface language.

Only new aircraft radio events are spoken. Loading a save never replays its old log. System diagnostics stay silent; leaving/backgrounding the duty clears audio. A new transmission immediately stops the previous playback and replaces any waiting transmission, across callsigns and urgency levels. One synthesis request can be in flight at a time. The app discards superseded audio and pauses new requests after rate limiting. It resumes with fresh transmissions after the wait. Expired or failed calls are skipped. A quiet push-to-talk click precedes the voice and a short squelch tail follows a completed transmission. Text radio and the simulation keep working. There is no repeat-last-transmission control.

## 3. GND: a departure from stand to takeoff

### Approve pushback

1. Select a parked departure.
2. Read the crew's pushback/start request and check nearby taxiing aircraft and the pushback area.
3. Approve pushback when clear. Let the maneuver complete; approving pushback is not a taxi or runway clearance.

### Build and issue a taxi route

1. Check the assigned runway and the current arrival/departure runway roles.
2. Choose **Select route** and click connected taxiway segments/junctions in sequence along the route you want.
3. Use **Undo** or **Clear** to revise the draft. You can also preview a suggested route when available.
4. Inspect the entire preview, including crossings and traffic moving toward it.
5. Press the action that **issues/publishes the taxi route**. A draft preview alone does not move the aircraft.

Faint map lines are chart guidance. **Purple** marks a route preview, **green** a cleared route, and the waiting/crossing indication has its own warning style. Main guidance remains visible; dense stand lead-ins become clearer at higher zoom. Stand numbers are labels, not a guarantee that every printed stand is available for simulation.

To change a moving aircraft's route, first instruct it to **Hold/Wait**, then construct and issue the replacement. Do not solve an opposing conflict by sending both aircraft farther into the same narrow segment.

### Runway operations

Crossing, line-up and takeoff are separate clearances. Taxi permission does not imply any of them.

1. Bring the aircraft to the appropriate holding position.
2. Inspect runway occupancy, arrivals and departures.
3. Issue a crossing clearance if the route requires it; wait for the aircraft to clear.
4. Issue line-up/enter-runway permission when appropriate.
5. Issue takeoff permission only when the runway sequence allows it.

The ground tag is hidden after takeoff clearance, but the aircraft's takeoff movement and runway occupancy continue to be simulated. It has not disappeared from the simulation simply because the tag is hidden.

### Arrivals and stands

Dim parked aircraft represent background turnaround occupancy. They carry no control tags and do not all request pushback at startup. Bright aircraft with tags are the controlled traffic. Source-chart parking endpoints support this background display; they do not automatically become approved operational stands. Existing stand capacity, route and occupancy checks still govern playable traffic.


Configure arrival/departure runway use in advance with the runway controls. Future flights use the allowed **ARR**, **DEP**, **MIX** or **CLOSED** roles. Closed or unsupported runways cannot be used as normal operating runways.

Arrivals can be announced automatically or arranged through the arrival action. Read the announced runway before touchdown. The aircraft rolls along the runway and follows a connected exit; after vacating, issue a taxi route to an eligible stand. Occupancy, aircraft dimensions, source support, carrier preferences and route feasibility affect stand assignment. Eligible terminal/contact stands are preferred where the airport's reviewed operational pool supports them; this does not create gates that have not been verified.

### Conflicts and tug recovery

When a predicted conflict is focused, inspect **both projected routes** and the **single conflict point**. Red expanding waves mark that point. Conflicting aircraft use the normal calling-aircraft pulse; their status labels stay steady.

Prevent a conflict by holding one aircraft early and routing the other clear. For an already blocked pair, the available **Call tug** action can arrange supervised retreat. The tug takes **60 simulated seconds** to arrive, has a **180-second dispatch cooldown**, and costs **five satisfaction points**. Keep the protected aircraft held during recovery. Release the other traffic only after the retreat completes and the route is clear.

## 4. APP: sequence and approach an arrival

### Separate the background from the clearance

The top procedure selector changes what is drawn behind the traffic: runway, arrival, approach or departure procedure. It does **not** assign that procedure to a flight. Use the selected-aircraft action, such as **Assign/Join procedure**, to issue an actual clearance.

APP includes both arrivals and departures. An arriving flight needs sequencing and a supported approach. A departure needs its SID/exit conditions monitored and an appropriate area handoff.

### Heading, altitude and speed

1. Select the flight and inspect its origin, destination, phase, current procedure and cleared values.
2. Enter **HDG**, **ALT** or **IAS**, then commit that field with **SET/Enter**.
3. Use **VECT** for a map-based heading. It sends one successful instruction and then switches off.
4. For direct navigation, choose an appropriate fix and press **DCT**. To follow a supported procedure, issue the procedure clearance explicitly.
5. Read the crew response and follow the aircraft's movement. Monitor separation while the aircraft turns or slows.

Plus/minus controls first snap an off-grid value to the next grid boundary in the requested direction. For example, **1,044 → 1,000 → 900** when decreasing altitude, and **1,044 → 1,100 → 1,200** when increasing. Altitude steps are **100 displayed units**, IAS steps **10 kt**, and heading steps **5°**, with wrap through north.

Reviewed altitude and speed constraints appear with their associated displayed fixes when that procedure context is visible. Crews can also call about an approaching unmet restriction. Do not use one procedure's constraint to justify a conflicting clearance on a different procedure.

### ILS: a complete sequence

There is no universal capture altitude or speed for every airport and runway. Use that runway's supported procedure, the displayed restrictions and the selected-flight ILS status.

1. **Check eligibility.** The flight must be approaching the correct airport/runway with a supported ILS context. A nearby-airport reference symbol does not install its approach. Closed runways or reference-only approaches are not valid substitutes.
2. **Position for the localizer.** Use a sensible intercept from the approach side with enough distance to turn, at the procedure's allowed altitude and speed. Read lateral deviation and distance in the ILS panel.
3. **Issue ILS clearance.** If the panel shows a source-defined arming gate, continue the cleared procedure to that gate. For example, a gate may prohibit early arming even though the ILS exists.
4. **Establish LOC.** The aircraft first follows the localizer laterally. It holds the assigned altitude while waiting for the glideslope.
5. **Capture GS from below.** Keep the aircraft below the glideslope until it intercepts. Once captured, the simulated aircraft follows it down. The ILS block shows independent **CLR**, **LOC** and **GS** indicators; they represent actual clearance/capture states. Do not command an arbitrary very low altitude to force capture.
6. **Confirm both captures.** In APP the target turns green after **both LOC and GS** are captured, unless a warning color takes priority.
7. **Complete the tower transfer.** Request handoff, wait for acceptance and then use the explicit **Transfer/Contact tower** action. Tower landing clearance is separate from ILS capture and is handled by the adjacent simulated unit.

A new heading, direct clearance, manual altitude or a go-around can cancel ILS. Read the cancellation notice. An emergency does not automatically grant ILS to an unsupported runway or wrong destination; use the appropriate return/diversion coordination first.

### If it will not capture or goes around

| What you see | What to check |
|---|---|
| ILS unavailable | Correct destination/return context, selected runway, runway status and whether ILS is supported. |
| Clearance pending | Published arming gate or required procedure segment. |
| LOC not established | Approach side, distance, lateral deviation, heading/intercept and speed. |
| LOC captured, GS waiting | Aircraft must intercept the glideslope from below; inspect the height difference and allowed capture window. |
| Unexpected acceleration | Compare actual IAS with cleared IAS and active restrictions; do not compare IAS directly with tag GS. |
| Go-around | Read the reported reason: completed transfer, landing clearance, runway occupancy and approach status are separate checks. |

After a go-around, keep separation, monitor the supported missed-approach path, establish a new safe sequence and issue the next clearance when valid. Repeatedly pressing ILS does not fix a poor intercept or incomplete handoff.

## 5. APP departures and ACC transfer

For a departure, inspect the assigned SID and **exit fix**, not just the destination airport. Arrange the required altitude and spacing, coordinate with the receiving area unit, wait for acceptance, then instruct contact and monitor check-in. If the exit route or agreed altitude changes, recheck the coordination conditions.

## 6. ACC: accept, control and transfer

ACC contains overflights as well as airport arrivals and departures. A flight's **destination airport** and **sector exit fix** are different fields.

1. Open the plan or transfer information and identify origin, destination, entry, intended exit and agreed altitude.
2. Accept an incoming coordination request when capacity, weather, entry compatibility and separation allow it. A rejected request remains pending with a reason; manual admission is independent of the automatic spawn timer.
3. Select the aircraft. Use heading, altitude, IAS, direct-to or holding instructions to meet the exit conditions and maintain spacing.
4. Inspect weather, terrain and special-use airspace before shortening a route. Background sector lines are guidance, not an automatic clearance.
5. Request outbound transfer near the appropriate exit under the agreed conditions.
6. Wait for acceptance, instruct the flight to contact the next unit, and monitor its check-in. Leaving the visible map alone does not complete the transfer.

The displayed sector is a training configuration. It must not be interpreted as the complete real FIR boundary or an actual inter-unit coordination agreement.

## 7. Weather, terrain and emergencies

**WX** controls the precipitation overlay. Green, yellow and red show progressively stronger simulated precipitation. Ordinary cloud or fog is not painted as a rain echo. Cells drift, develop and dissipate with simulation time; pausing also pauses their evolution. ATIS/weather provides wind, gusts, visibility, cloud base and QNH. No live weather feed is fetched.

Bad weather can slow ground movement, reduce admissions and increase spacing. Aircraft already airborne remain your responsibility: use speed control, vectors, holding or a coordinated diversion rather than expecting the weather setting to reroute them.

Terrain contours and selected high points provide context. Terrain/minimum-altitude warnings require attention. Keep supported minimum altitudes and procedure restrictions; a smoothed map line is not a higher-resolution elevation survey. In high-elevation scenarios such as Lhasa, airport elevation and procedure restrictions are substantial—do not reuse lowland approach altitudes.

A flashing aircraft may be making a proactive call. Select it and read the request in the radio log. Check the actual route and current conditions before approving a direct, speed, altitude or weather request. Calls are contextual, not instructions you must accept.

Use **Special coordination** for appropriate priority, emergency services, return-to-field or diversion actions. **7700** distress and **7600** communication failure have different meanings. Choosing an alternate is only a selection; confirm the coordination and continue to issue safe clearances. Rejecting a request or canceling a return does not magically remove an emergency.

## 8. Score, pause and save

Safety, communication and coordination contribute to the displayed satisfaction/service rating. Unresolved safety events and overdue reasonable requests can affect it. Necessary weather holding and refusing an unsafe request should not be treated as arbitrary penalties. Tug recovery has its stated cost.

Use **⌘P** to pause, **⌘S** to save and **⌘⇧H** to save and return home. The game also saves progress locally during normal use. Continue the same airport/position to resume. GND and the air simulation do not form one automatically continuous shared aircraft world.

| Shortcut | Action |
|---|---|
| ⌘P | Pause/resume |
| ⌘S | Save the current session |
| ⌘⇧H | Save and return to the main menu |
| ⌘/ | Reopen the tutorial/manual |
| ⌃⌘F | Toggle fullscreen |
| ⌘1 / ⌘2 / ⌘3 | Choose GND / APP / ACC from the menu when not in a duty |

For a first practice session, use light traffic, approve one pushback, issue one checked taxi route and complete a departure. Then try APP with a supported ILS arrival, and ACC with one complete accept/contact/transfer cycle.

## Conflict forecast in v1.1

For a selected conflicting air pair, dashed projections and future positions distinguish the forecast from the cleared route. The panel shows estimated time until the lateral and vertical minima are simultaneously lost. The forecast uses current horizontal motion and altitude changes capped at the cleared level; it does not predict every future route turn or pilot action. Parallel traffic can therefore generate a forecast when vertical convergence is the problem, while a safe level-off avoids a false extrapolated conflict.
