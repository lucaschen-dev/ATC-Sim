# v1.1.1 / build 50 verification

Checked on 2026-11-10. This update changes presentation and adds optional radio speech; it does not replace the airport navigation database or flight model.

## Automated and native display checks

- The release build succeeds and the installed signed app retains App Sandbox. Outbound networking is enabled for the optional user-configured voice service. No microphone permission is requested.
- Nineteen airport packages keep their identifiers, routes and save locations, with unique fictional names in Chinese and English.
- The final native display harness produces 54 hidden-window captures, including all 19 ground airports at overview and detail scales, bilingual settings/cards/setup, approach weather and area tags. Its 123 checks pass. This is broad display screening, not a new survey of every airport corner.
- The same simulated weather field produces six closed contour bands. Tests check finite geographic geometry, closure, motion, pan and scale behavior, and no echoes for non-precipitating conditions. Approximately 59,572 samples are prepared in about 50 ms on the development Mac, away from the UI thread. This is preparation time, not a compositor FPS measurement.
- 112 aircraft scale and label checks pass and cover map distance, airframe ratios, type families, rotation, clickable wings/nose and label exclusions. A convergence regression checks that two automatic attached tags yield rather than overlap. Background parked aircraft use actual map scale rather than active-target readability enlargement. Collision physics remains independent of the rendered symbol.
- A parked fleet is cached per airport; source stand endpoints are unique, controlled/assigned stands suppress background aircraft, and scenery generates no radio calls or controlled traffic. Coverage is limited to trustworthy source endpoints; it does not fill every printed stand.

## Voice checks and listening boundary

- Fourteen queue checks pass: saved history stays silent, new events are spoken once, diagnostics remain silent, waiting audio is bounded/expired, emergencies take priority, and leaving a duty clears audio.
- Twenty-eight cloud/phonetic checks pass with mocked responses: aviation digits, fixed HTTPS request host, header-only credentials, language/model request, rejected path injection, 401/403/402/429/500 handling without automatic retries, audio-type validation and male-voice filtering.
- A unique disposable Keychain entry was saved, replaced, read and removed. It was not a real API key.
- The installed settings show concealed key input, Chinese/English male-voice choices, manual IDs, auditions, rate and urgency. With no key configured, speech is off and paid-generation actions remain unavailable.
- **No paid cloud audio was generated or listened to with a real user key.** Naturalness, accent, pronunciation and latency still need a player audition. The earlier local system-voice audition was rejected and is not the production backend.
- Cloud output sends radio text to ElevenLabs and uses the player’s account. Failures do not change clearances or stop text radio. There is no microphone input and no replay-last-message control.

## Installed-window and player-state acceptance

Actual window checks cover home video, airport cards and loading transition, settings in both languages, ground pushback/scale/follow controls, and approach weather/aircraft selection. An IAS 200 clearance is read back and a runway 19L ILS clearance establishes LOC. This run stops before GS capture or tower transfer. Continuous drag and live FPS remain outside the established tool evidence; no claim of universal elimination of stutter is made. All 32 original player files are restored and rechecked byte-for-byte after relaunch; all original sandbox preference values match. A test-only approach review file is archived privately. The game is left open at the home screen.

The bundle contains the existing menu radar video, no old watercolor loading PNGs and no PDFs. Public delivery contains English documentation and own-game images only. No app, installer, private code, chart data, API key or player save is published.
