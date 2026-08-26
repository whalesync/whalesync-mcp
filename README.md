# Whalesync MCP server

[Whalesync](https://www.whalesync.com) keeps data in two-way sync between the tools your team
already uses — Airtable, Webflow, HubSpot, Salesforce, Notion, Postgres, and more.

This repository is the public home of the **Whalesync MCP server**: a remote
[Model Context Protocol](https://modelcontextprotocol.io) server that lets AI agents build and
manage syncs for you — create a sync between two apps, map tables and fields, turn it on, and
monitor it, including answering "why isn't this record syncing?".

- **Server URL:** `https://api.whalesync.com/mcp` (Streamable HTTP)
- **Auth:** OAuth 2.1 with PKCE — your client opens a browser to approve access; no API keys to
  paste. Read-only access is available at consent time.
- **Docs:** https://docs.whalesync.com/api/mcp

The server is remote-only. There is nothing to install from this repository — it exists so
directories and registries can link to a canonical public source. The server itself is developed
elsewhere.

## Install

**Cursor** — [Add to Cursor](https://cursor.com/install-mcp?name=whalesync&config=eyJ1cmwiOiJodHRwczovL2FwaS53aGFsZXN5bmMuY29tL21jcCJ9), or add to `~/.cursor/mcp.json`:

```json
{ "mcpServers": { "whalesync": { "url": "https://api.whalesync.com/mcp" } } }
```

**Claude Code**

```bash
claude mcp add --transport http whalesync https://api.whalesync.com/mcp
```

**VS Code**

```bash
code --add-mcp '{"name":"whalesync","type":"http","url":"https://api.whalesync.com/mcp"}'
```

**Codex**

```bash
codex mcp add whalesync --url https://api.whalesync.com/mcp
```

**claude.ai / ChatGPT** — add a custom connector with the URL `https://api.whalesync.com/mcp`.

On first use, your client opens a browser window to sign in to Whalesync and approve access.
You'll need a [Whalesync account](https://www.whalesync.com).

## What the agent can do

24 tools over the Whalesync public API:

- **Build**: `sync_create`, `sync_update`, `sync_list_connectors`, `sync_list_bases`,
  `sync_list_tables`, `sync_list_fields`, `sync_get_mappings`, `sync_update_mappings`,
  `sync_validate_mappings`
- **Run**: `sync_activate`, `sync_pause`, `sync_delete`
- **Monitor & fix**: `sync_get_status`, `sync_list_issues`, `sync_get_issue`,
  `sync_retry_issue`, `sync_list_operations`, `sync_get_operation`, `sync_search_records`,
  `sync_get_record_status`, `sync_list_pending_deletes`
- **Navigate**: `sync_list`, `sync_get`, `sync_whats_next`

Tools are prefixed `sync_` because they cover Whalesync's sync feature; other features will
arrive under their own prefixes.

Anything irreversible stays human-gated: connecting your apps (OAuth), starting a sync, and
approving deletes all happen in the Whalesync app — the agent hands you a link at each step.

## Support

- Docs: https://docs.whalesync.com
- Support: support@whalesync.com
- Privacy policy: https://www.whalesync.com/privacy-policy
