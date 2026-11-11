# ATC Sim v1.1.5 · Build 54

- The in-app GitHub form attaches the diagnostic ZIP once the form opens. Sign in there if prompted, review the draft, and choose **Create** yourself.
- Radio settings automatically load the account's available voices when needed and keep a local catalog of voice names and IDs. The current Chinese and English selections remain available while refreshing. The API key is kept in macOS Keychain.
- Dropdowns are drawn in the game window with a single border. Moving onto a menu keeps the green crosshairs at the size of that window.

Verified voice selection and persistence across an installed restart, and checked that the in-window dropdown keeps the full-size cursor. A local WebKit check verified file selection and that Create was left untouched. Live upload requires a signed-in GitHub session and was not exercised.

This release publishes documentation only.

[Bug reporting guide](../docs/BUG_REPORTING.md)
