# Model Radar

A macOS app that keeps a read-only inventory of the AI models used across your development folder. Point it at the folder; it finds every project, identifies the providers and models each one uses, keeps the dashboard fresh as you work, and checks whether those models are still current. Bring your own API key.

**[Download the latest release](https://github.com/scott-rippey/model-radar-app/releases/latest)**. The `.dmg` file is the installer; the other files on the release are the app's auto-update machinery. See what changed in each version: [CHANGELOG](CHANGELOG.md) or the [release notes](https://github.com/scott-rippey/model-radar-app/releases).

## Install

1. Download the `.dmg` from the latest release above.
2. Open it and drag **Model Radar** to Applications.
3. First launch: macOS shows the standard "downloaded from the internet" confirmation. Click Open.
4. In the app: choose your development folder, add an API key in Settings, and scan.

Install once. The app keeps itself current from this repository's releases automatically; a fresh download is only needed for a new machine.

Prefer one place for all the Power Your Process apps? **[Hangar Deck](https://github.com/scott-rippey/hangar-deck-app)** installs and updates Model Radar, CC Blackbox, and whatever comes next, and tells you when a new version lands.

Requires an Apple Silicon Mac on a recent macOS.

See the [user guide](user-guide.md) and [features](features.md).

## About

The application is signed and notarized. The source code is not published; this repository hosts installers and release notes only. Version history: [CHANGELOG](CHANGELOG.md).
© Scott Rippey. All rights reserved.
