# Model Radar user guide

## First launch

1. Open Model Radar. The first screen asks for your development folder. Click **Choose** and pick the folder that contains your projects (for example `App Development`). macOS may ask permission to read that location; allow it.
2. Click **Start first scan**. The free stage-one scan finds your projects and their AI evidence in a second or two. You land on the dashboard with grey, unverified model chips.
3. Go to **Settings > API keys**, click **Add key** next to Anthropic, paste your key, and press Save. Click **Verify** to confirm the provider accepts it.
4. Back on the dashboard, click **Rescan all**. Model Radar now identifies the models in each project. Chips turn teal, project summaries appear, and flags call out anything set at runtime.

You only add a key once; it is stored encrypted in your Keychain.

## Reading the dashboard

- Each card is one project. The header line shows the project name and, before the AI pass, how many grep hits it had.
- **Teal chip**: a verified model. Hover for provider, role, where it is specified, and confidence.
- **Amber chip**: low confidence. Open the project to read the evidence and decide.
- **Chip ending in `*`**: the model is set at runtime; the chip shows the default found in code.
- **Coloured dot on a chip**: the model's status from the last check (green current, amber deprecated, red not in the provider's list).
- **Flags** under the chips explain special situations, such as models stored in a database or model strings that are probably data rather than usage.
- **"changed"** or **"new"** on a card means the freshness sweep saw the project change since its last scan. Use **Rescan N changed** in the header, or the circular arrow on the card.

Click a card to open the project. Each model expands to show its evidence; click a file path to reveal it in Finder. **Dismiss** hides a finding you know is wrong; it stays dismissed through rescans and can be restored.

## Scanning

- **Rescan all**: re-runs everything. Projects whose evidence has not changed are skipped in the AI stage, so a rescan is usually fast and cheap.
- **Scan a folder**: pick any folder inside your development folder and scan just that. Use it right after adding a new project.
- **Rescan project**: from a project card or the project page.
- **Cancel** stops a running scan; projects already finished keep their new data.

Settings > Scanning lets you pick which provider and model do the identification. Anthropic is the default. Other providers become available as soon as you add their key; their model suggestions come from the Models view after you refresh the provider lists.

## Keeping it fresh

Model Radar checks your projects for changes when it starts and every 30 minutes while it is open. It never runs while the app is closed. Changed projects get a badge; you decide when to spend an AI request on them. If you would rather have that happen automatically, turn on **Rescan changed projects automatically** in Settings > Scanning.

## Models view

**Refresh provider lists** pulls the current model list from every provider you have a key for. **Check model status** compares the models your projects use against those lists. Anything missing from its provider's list is marked, and a web search adds the announcement details and the replacement when one exists. The same status dots then appear on the dashboard chips.

## Chat

Open **Chat** and describe what you want, for example:

- "I just added Personal/Invoice Bot. Look at it and record what models it uses."
- "Which projects still use claude-3-5-haiku?"
- "Read the AI client in SOP Admin and tell me if the model can be changed at runtime."

The assistant can list folders, search with ripgrep, and read files, all read-only. The only thing it can write is a finding into the inventory, and each one shows up as a chip in the transcript and on the dashboard. Chats are saved in the left sidebar.

## Settings

- **Font size** scales the entire app. **Glass window** makes the window transparent so your desktop shows through; it re-opens the window when toggled.
- **API keys**: add, replace, verify, or remove a key per provider. If the Keychain can no longer decrypt the key store (this can happen after a macOS password reset), the card offers a reset; the old file is kept as a backup.
- **Database**: where the inventory lives, its size, and row counts. Reveal it in Finder if you want to back it up.
- **Updates**: the current version and a manual check. Updates download in the background; they apply when you quit the app or choose Model Radar > Restart to Update.
- **System health**: quick status of the folder, bundled ripgrep, database, and Keychain.

## Exporting

**Export CSV** on the dashboard writes every finding with its project, customer, provider, model, role, where it is specified, confidence, and dismissed state.

## Privacy

Your code stays on your Mac. The AI stage sends only the matched lines and a few lines of context around them. Keys never leave the Keychain except in the calls you trigger to that provider. The app cannot write into your development folder.
