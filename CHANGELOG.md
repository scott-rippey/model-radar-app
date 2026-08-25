# Changelog

<!--
Newest first. Mirror each release's notes into the public repo's CHANGELOG.md.
### New / ### Improved / ### Fixed
-->

## 1.0.0

First release.

### New

- Scans a development folder read only, finds every project, and identifies the AI providers and models each one uses.
- Dashboard grouped by customer and project, with evidence for every model and flags for models that are set at runtime.
- Freshness sweep on launch and every 30 minutes while open: changed and new projects are badged, and can be rescanned with one click or automatically.
- Chat assistant with read-only tools for targeted scans ("go look at this folder").
- Models view: pulls each provider's live model list and checks whether the models you use are still current.
- Bring your own key for Anthropic, OpenAI, Google, and xAI, stored in the macOS Keychain.
- CSV export, font size slider, glass window mode.

### Privacy and safety

- Model Radar never writes to your development folder. Reading is the only thing it can do there, and that is built into the structure of the app rather than left to good behavior.
- Files that look like secret stores (.env files, keys, certificates, credentials files) are never read, searched, or sent anywhere. Anything shaped like a key inside ordinary source is masked before it leaves your Mac.
- Scanning sends only the matched lines and a little surrounding context. A scan never uploads whole files.
- Chat answers render as plain text and links are never clickable, so nothing the assistant writes can carry your information anywhere by being clicked.
