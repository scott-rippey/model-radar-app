# Model Radar features

What is running today. No changelog here; version history lives in `CHANGELOG.md` in the public releases repo (model-radar-app).

## Scanning

- **Point it at one folder.** Model Radar walks your development folder and treats any subfolder with `package.json`, `CLAUDE.md`, `.git`, `deno.json`, or `pyproject.toml` as a project. Build output, `node_modules`, worktree copies, vendored repos, and media files are skipped.
- **Code only.** Markdown is never scanned; a model name in documentation does not count as usage. Your own ignore rules (Settings > Scan ignores) skip further files or folders, and they narrow chat search too.
- **Two stage scan.** Stage one runs a bundled copy of ripgrep over each project with a curated pattern set (model IDs such as `claude-`, `gpt-`, `gemini-`, `grok-`, `text-embedding-`, `eleven_`, plus SDK imports, provider endpoints, model constants, and key names). It runs in well under a second across dozens of projects and costs nothing. Stage two sends the grep hits, with a few lines of context around each, to the AI provider you chose and gets back a structured inventory: provider, model, role (chat, embedding, speech, image, video), where it is specified, confidence, evidence, and notes.
- **Cheap rescans.** Every project keeps a fingerprint of its evidence. A rescan re-runs stage one (free) and only spends an AI request on projects whose evidence changed.
- **Honest about the tricky cases.** Models that live in a database setting, a per-run config file, or a remote catalog are flagged as runtime configurable, with the code default shown. Projects whose model strings are data rather than usage (telemetry, fixtures, price tables) are flagged so you do not mistake them for deployments.
- **Scoped scans.** Rescan one project, or pick any folder inside the root and scan just that.

## Dashboard

- Projects grouped by customer, then personal projects, then everything else.
- One chip per model with a status dot (current, deprecated, retired), a `*` for runtime-configurable models, and amber for low-confidence findings. A legend above the cards explains every color.
- A red retired counter in the window header shows at a glance how many models in use have been retired, with no scan needed. It clears only when a rescan shows the code no longer uses them.
- Click any project for the full detail: summary, flags, each model with its evidence (file and line, revealed in Finder with one click), the raw grep hits, and dismiss/restore for false positives. Dismissed findings survive rescans.
- Export the whole inventory as CSV.

## Freshness

- On launch and every 30 minutes while the app is open, Model Radar compares each project's files against the last scan and badges changed projects; brand new project folders show up as "new".
- "Rescan N changed" runs the hybrid scan on just those. A setting lets it happen automatically; it is off by default because it spends your API key.
- Nothing runs in the background when the app is closed.

## Models view

- Pulls the live model list from every provider you have added a key for (Anthropic, OpenAI, Google, xAI).
- "Check model status" compares every model your projects use against those lists. Models missing from a provider's list are flagged, and one web search request (through your Anthropic key) adds the deprecation or retirement context and the suggested replacement.
- Hover any model in "Models your projects use" to see exactly which projects use it.

## Chat

- Ask about the inventory or point the assistant at a folder: "I just added Customers/Acme/portal, go look at it and record what it uses."
- The assistant has three read-only tools (list a folder, search with ripgrep, read a file range) and exactly one write tool, which records a finding into Model Radar's own database. It can never modify a file in your development folder.
- Every tool call shows up in the transcript. Chats are saved and can be resumed or deleted. Each chat is bound to the development folder it was started in; after you change folders, older chats stay readable but cannot be continued.
- Chat uses your Anthropic key, and the model it runs on is selectable in Settings (Anthropic models only; the assistant is built on Anthropic tool calling).

## Keys and privacy

- Bring your own key for Anthropic, OpenAI, Google, and xAI. Keys are stored encrypted in the macOS Keychain, never in the database, and never shown again after you save them. Verify tests a key with the cheapest read-only call the provider offers.
- Scanning sends only short excerpts around each hit; a scan never uploads full files. Chat sends what the assistant reads to answer you (up to 400 lines per file read, 200 matching lines per search) to Anthropic, and refuses to read files that look like secret stores (.env files, keys, certificates, credentials files).
- Read-only by construction: the app has no code path that writes into the scanned folder.

## Settings

- Font size with a live preview on the card and one-click Apply for the whole app; the top bar holds its size.
- Glass window: a transparent window that shows the desktop behind the app.
- Provider and model used for scanning, and the Anthropic model used by chat.
- Scan ignores: your own glob rules the scan and chat search skip.
- Database card: location, size on disk, row counts, reveal in Finder.
- System health: development folder, bundled ripgrep, database, Keychain encryption, key store.
- Updates: current version, check for updates. Updates download in the background and apply when you quit.

## Requirements

Apple Silicon Mac on a recent macOS, and at least one provider API key for the AI stage. The free stage-one scan works with no key at all.
