# Omnido — releases

Public distribution channel for **Omnido**, a macOS menu-bar app that captures a
task from any window together with its source and jumps back to that source
later. The application source lives in a separate, private repository; this repo
holds only the built releases and their notes.

## Download

Grab the latest Apple Silicon build from
[Releases](https://github.com/SaschaHenning/omnido-releases/releases):

- `Omnido-<version>-arm64-mac.dmg` — open it and drag **Omnido** into
  **Applications**.

No GitHub account or token is needed — the releases are public. The app is
Developer ID signed and notarized, so it opens without a Gatekeeper prompt.

## Updates

The app checks this repository for newer versions on its own and installs them
on the next quit or after „Neu starten" in the menu — no token, no manual
download. Each release carries `Omnido-<version>-arm64-mac.zip` (the archive the
in-app updater downloads), its `.blockmap` and `latest-mac.yml` (the update feed).

## What is not here

No source code and no build pipeline — those stay in the private repository.
This repo is releases only.
