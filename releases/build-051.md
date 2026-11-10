# ATC Sim v1.1.2 · Build 51

- A new radio transmission interrupts the one in progress, regardless of callsign or urgency. Pending audio generation for the previous transmission is cancelled in the app.
- Each transmission begins with a brief push-to-talk click. A short squelch tail follows completed speech. When interrupted, the previous transmission cuts off immediately.
- Both effects are bundled locally and follow the radio volume setting. The speech-rate control applies to the voice.
- Text radio retains every transmission and stays available when speech is off.

Verified the signed macOS build, the installed home screen, and both bundled sound files. Live ElevenLabs playback is pending. This release publishes documentation only.

[Full player guide](../docs/HOW_TO_PLAY.md)
