# Changelog

<!--
Newest first. Mirror each release's notes into the public repo's CHANGELOG.md.
### New / ### Improved / ### Fixed
-->

## 1.1.3

### Improved

- Expanding a model on a project page now shows the evidence lines that actually contain that model first, with context lines after, so you can see at a glance where an identification came from.
- The Raw evidence list has a filter box: type any model id, file name, or text and the list narrows instantly.

## 1.1.2

### Improved

- Saving a change to Scan ignores now marks every project as changed, so one click of Rescan changed applies the new rules everywhere. Previously the rules waited for a full rescan without saying so.
- The "changed" language is clearer everywhere: the button reads "Rescan N changed projects", the check result names projects, and hovering a changed, new, or missing badge on a card explains exactly what it means and what a rescan will do.

## 1.1.1

### Improved

- After an update that changes the scan rules, every project is marked changed automatically, so one click of Rescan changed refreshes all the evidence. You no longer need to know to run a full rescan.
- Project titles stay distinct when two projects would share nearly the same name; the qualifier that tells them apart is kept instead of being trimmed away.
- The Models view section is now titled "Available models by provider" and explains what it shows: everything each provider offers right now, pulled live. Provider lists start closed and open individually.
- Expanding lists use a rotating chevron everywhere.
- Check for changes now reports its result right in the toolbar, including "No changes found", instead of finishing silently.
- Evened out the spacing around the dashboard legend.

## 1.1.0

### New

- Scan ignores in Settings: add your own skip rules, one glob per entry (for example *.txt or runs/**). They apply to scans and to the chat assistant's searches, and they can only narrow the scan, never widen it.
- Chat model picker in Settings: choose which Anthropic model the assistant uses.
- Retired models counter: a red count in the window header shows how many models still in use have been retired by their provider, with no scan needed. Click it to open the Models view.
- Hover any model in the Models view to see which projects use it.
- A legend on the dashboard explains every chip color, status dot, and marker.

### Improved

- New blue look across the whole app, with a matching app icon.
- One consistent header: the app name, project counts, and navigation stay put in every view, and the bar keeps its size at every font setting.
- Models view is two columns; provider lists start open and collapse individually.
- Chat is wider, with an input that grows as you type and a cleaner send button.
- Settings cards pack into two tight columns, and the font size slider previews on its own card with an Apply button that resizes the whole app.
- Markdown files no longer count as model usage. Documentation describes models; it does not run them. Rescan once and documentation-only entries clean themselves up.

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
