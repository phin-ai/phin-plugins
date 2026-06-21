# Phin — Claude Code plugins

The official Claude Code plugin marketplace (`phin-official`) for **[Phin](https://github.com/phin-ai/phin)**, the AI-native data workbench for macOS.

## phin-mcp

Query your saved Phin database connections — Postgres, MySQL, SQLite, MongoDB — directly from Claude Code: list connections, browse schemas, describe & preview tables, and run **read-only** SQL or MongoDB queries. Read-only by default; your passwords stay in the macOS Keychain and are never sent to the model.

### Install

```
/plugin marketplace add phin-ai/phin-plugins
/plugin install phin-mcp@phin-official
```

Then run `/mcp` to confirm the `phin` server is connected.

> **Requires Phin** installed at `/Applications/Phin.app` — the plugin points at the `phin-mcp` binary that ships inside the app. [Download Phin](https://github.com/phin-ai/phin/releases/latest).
>
> Installed Phin somewhere else? Use Phin's **Settings → Claude Code → Install** button instead — it registers the server at the binary's real path, wherever Phin lives.

See [`phin-mcp/README.md`](phin-mcp/README.md) for the full tool list and safety details.
