# Phin Data Workbench — Claude Code plugin

Query your saved [Phin](https://github.com/phin-ai/phin) database connections
(Postgres, MySQL, SQLite, MongoDB) directly from Claude Code.

## Prerequisites

**Install Phin first.** This plugin is a thin pointer to the `phin-mcp` binary
that ships inside `Phin.app`. If Phin isn't installed at
`/Applications/Phin.app`, the server will report **Failed to connect** in
`/mcp`.

> Installed Phin somewhere else? Use Phin's built-in **Settings ▸ Install
> Claude Code integration** button instead — it registers the server at the
> binary's real path, wherever Phin lives.

## Install

```
/plugin marketplace add phin-ai/phin-plugins
/plugin install phin-mcp@phin-official
```

Then restart Claude Code (or run `/mcp`) to confirm the `phin` server is
connected.

## Tools

| Tool | What it does |
| --- | --- |
| `list_connections` | List saved connections (id, name, kind, host, db, env). Never returns secrets. |
| `list_schemas` | Browse the schema / table / collection tree for a connection. |
| `describe_table` | Columns, indexes, foreign keys, row count for one table. |
| `preview_table` | First N rows of a table or collection (default 50). |
| `run_query` | Run a **read-only** SQL query. Writes are refused. |
| `mongo_find` | Run a find / aggregate against a MongoDB connection (read-only). |

## Safety

- **Read-only by default.** `INSERT` / `UPDATE` / `DELETE` / DDL and Mongo
  `$out` / `$merge` are refused. To permit writes, the server must be started
  with `--allow-writes` (not enabled by this plugin manifest).
- **Secrets stay in the macOS Keychain.** Passwords are never sent to the model
  or written to disk.
- Results are size-capped (row limits + per-cell truncation) so a wide query
  can't exhaust the context window.
