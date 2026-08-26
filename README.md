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

**Claude (web, desktop, mobile)** — [install from the Claude directory](https://claude.ai/directory/whalesync) — click **Connect**.

**ChatGPT** — add a custom connector with the URL `https://api.whalesync.com/mcp`.

**Grok** — [grok.com/connectors](https://grok.com/connectors) → New Connector → Custom → paste `https://api.whalesync.com/mcp`.

On first use, your client opens a browser window to sign in to Whalesync and approve access.
You'll need a [Whalesync account](https://www.whalesync.com).

## What the agent can do

24 tools over the Whalesync public API:

- **Build**: `create_sync`, `update_sync`, `list_connectors`, `list_bases`, `list_tables`,
  `list_fields`, `get_mappings`, `update_mappings`, `validate_mappings`
- **Run**: `activate_sync`, `pause_sync`, `delete_sync`
- **Monitor & fix**: `get_sync_status`, `list_issues`, `get_issue`, `retry_issue`,
  `list_operations`, `get_operation`, `search_records`, `get_record_status`,
  `list_pending_deletes`
- **Navigate**: `list_syncs`, `get_sync`, `whats_next`

Anything irreversible stays human-gated: connecting your apps (OAuth), starting a sync, and
approving deletes all happen in the Whalesync app — the agent hands you a link at each step.

## Support

- Docs: https://docs.whalesync.com
- Support: support@whalesync.com
- Privacy policy: https://www.whalesync.com/privacy-policy
