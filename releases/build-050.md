# ATC Sim v1.1.1 — Build 50

Fictional airport presentation, radar color hierarchy, ground display and radio speech. Release date: 2026-11-10.

## Airport presentation

- Nineteen bundled airports now use fictional display names with varied naming styles. Other valid airport codes also receive consistent fictional display names.
- Existing four-letter codes, routes, geometry, CSV identifiers and save locations are retained.
- Airport cards and their expanding loading transition use black-and-white dry-paint lettering. Previous watercolor assets are excluded from the installed bundle.
- The home screen keeps its existing looping approach-radar video. Seat setup retains the softened video background. Seat loading still shows the airport code and English position name with the bottom progress bar.

## Radar and ground

- Muted blue callsigns, green flight values and violet neighboring traffic provide hierarchy; gold selection and safety warnings keep their priority. Ground aircraft remain yellow.
- Precipitation uses six continuous, closed contour levels. Geographic weather shapes are prepared away from the UI thread, reused across pans, and reprojected at the new scale. They evolve with the existing simulated weather field. Cloud/fog alone do not produce rain echoes.
- Quiet parked turnaround airframes populate genuine source-chart stand endpoints, with a high terminal occupancy and lighter remote occupancy. They do not create a burst of controlled traffic or radio calls. Controlled flights take visual precedence at their occupied/assigned stands.
- Automatic ground tags keep their attachment while clear and yield when nearby aircraft or zoom clamping would overlap labels. Manually dragged labels stay under player control.
- Ground pavement and parking guidance are darker and subordinate to terminals, aircraft and active clearance routes. Existing geographic geometry is retained.
- A common overview readability scale preserves type-relative aircraft size. Close views follow aircraft length and wingspan without an upper screen-size cap. Distinct simplified silhouettes cover twin-engine jets, four-engine jets, regional jets, business aircraft and turboprops. Click footprints follow the rendered shape, while collision protection remains independent of display size.

## Radio speech

- Optional ElevenLabs v3 output for new aircraft radio events in GND, APP and ACC. Silent by default until the user supplies a key, chooses voices, auditions and enables speech.
- Concealed API-key input with save, replace and remove actions; credentials remain in macOS Keychain, outside player saves, preferences and exported diagnostics.
- Separate Chinese/English male-voice selection, voice-list loading, manual Voice IDs, language auditions, emergency audition, contextual urgency, volume and local playback rate (initially 1.15×). No repeat-last-transmission action.
- Airline telephony names and explicit radio digit pronunciation for callsigns, headings, IAS, runway identifiers and frequencies; Chinese height quantities remain readable.
- Saved radio history never replays. Backgrounding/leaving the duty clears audio. Urgent calls supersede waiting routine calls, the four-message queue expires old calls, and delayed responses are discarded. Network failures leave text radio available and do not automatically retry paid synthesis.
- Cloud output requires an ElevenLabs account and usage charges. Actual cloud voice quality has not been accepted in a paid live audition yet; no personal key was supplied during verification. The earlier local system voice audition was rejected and is not the production speech backend.

## Validation and delivery

Release build, 19-airport native display screening, Chinese/English UI captures, geographic-contour checks, type-size/hit-footprint checks, speech queue regressions, mocked cloud responses and a Keychain save/replace/remove round trip were checked. No paid cloud generation was performed. Installed-window acceptance and save preservation are described in [the build 50 validation note](../docs/V1_1_1_VALIDATION.md).

**Documentation-only release:** no app, installer, private source, charts/PDFs, system voice files or player saves are attached. GitHub's automatic source archives contain this public documentation repository only.

[Full player guide](../docs/HOW_TO_PLAY.md)
