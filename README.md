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

## MCP server

Omnido has an MCP server, so AI clients such as Claude Code can read and write your tasks.

- Endpoint: `https://omnido.saschahenning.de/mcp` (Streamable HTTP, stateless)
- Sign-in: a personal access token, sent as `Authorization: Bearer omn_…`. Create it in the web
  app under Einstellungen → „Omnido in anderen Apps". A read-only right is available; a
  read token does not see the write tools.
- Tools: `search_tasks`, `list_tasks`, `get_task`, `create_task`, `update_task`, `complete_task`,
  `add_capture`, `get_settings`, `update_settings`, `get_profile`, `update_profile`,
  `remove_profile`, `list_categories`, `create_category`, `update_category`, `remove_category`,
  `list_mcp_connections`, `create_mcp_connection`, `update_mcp_connection`,
  `remove_mcp_connection`. Tasks cannot be deleted over MCP.
- Isolation: every tool runs for the token's owner only; ids of other users answer `NOT_FOUND`.

Claude Code:

```sh
claude mcp add --transport http --scope user omnido https://omnido.saschahenning.de/mcp \
  --header "Authorization: Bearer <token>"
```

## What is not here

No source code and no build pipeline — those stay in the private repository.
This repo is releases only.
