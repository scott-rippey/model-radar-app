# Changelog

<!--
Newest first. Mirror each release's notes into the public repo's CHANGELOG.md.
### New / ### Improved / ### Fixed
-->

## 0.1.0

First build.

### New

- Scans a development folder read only, finds every project, and identifies the AI providers and models each one uses.
- Dashboard grouped by customer and project, with evidence for every model and flags for models that are set at runtime.
- Freshness sweep on launch and every 30 minutes while open: changed and new projects are badged, and can be rescanned with one click or automatically.
- Chat assistant with read-only tools for targeted scans ("go look at this folder").
- Models view: pulls each provider's live model list and checks whether the models you use are still current.
- Bring your own key for Anthropic, OpenAI, Google, and xAI, stored in the macOS Keychain.
- CSV export, font size slider, glass window mode.
