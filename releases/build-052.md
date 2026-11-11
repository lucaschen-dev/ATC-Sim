# ATC Sim v1.1.3 · Build 52

- The radio switch sits at the top of the redesigned panel and keeps its previous setting across launches and configuration changes. The account key remains in this Mac’s Keychain.
- A new call immediately interrupts playback. Rapid updates retain only the latest pending transmission and allow one cloud synthesis request at a time. Temporary throttling delays new requests and expired calls are skipped.
- The low-latency v4 Turbo model is the default. Eleven v3 remains selectable. Playback supports up to 2×, with shorter, quieter push-to-talk and squelch sounds.
- All 19 airports use clearer taxiway markings and earlier, scale-based stand guidance. VHHH and VMMC were compared directly with the preceding display. The airport source and taxi routing files are unchanged.
- Ground aircraft have revised swept wings, tails and tapered nacelles, with separate narrowbody, widebody, four-engine, regional, business and turboprop silhouettes.

Verified the installed settings layout and retained Keychain and switch state. Reviewed overview and detail renders for all 19 airports. No live ElevenLabs request was sent during verification.

This release publishes documentation only.

[Full player guide](../docs/HOW_TO_PLAY.md)
