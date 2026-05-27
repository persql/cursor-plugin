# PerSQL for Cursor

[PerSQL](https://persql.com) gives every agent, every PR, and every app its own isolated SQLite database. This plugin wires the hosted PerSQL MCP server into Cursor and ships two slash commands and a rule that encode the branch-first workflow.

## What you get

- **MCP server** at `https://mcp.persql.com` exposing the full PerSQL toolset: `query`, `batch`, `propose_mutation`, `apply_mutation`, `claim_branch`, `merge_branch`, `list_snapshots`, `restore_snapshot`, `restore_to_time`, schema docs, NL-to-SQL via `ask`, and more.
- **`/persql-branch`** — claim a fresh branch with a scoped token in one step.
- **`/persql-rollback`** — restore to a snapshot or point in time, with a branch-first safety net.
- **Branch-first rule** that biases the agent toward isolated experiments instead of destructive operations on the live database.

## Install

1. Install from the [Cursor Marketplace](https://cursor.com/marketplace) (or clone this repo and reference it locally).
2. Sign in at [console.persql.com](https://console.persql.com) and create a token under **Tokens**.
3. Set the token as an environment variable in your shell:
   ```sh
   export PERSQL_TOKEN=psql_live_s0_...
   ```
4. Reload Cursor. The `persql` MCP server should appear in **Settings -> MCP**.

## Configuration

The plugin ships with `mcp.json`:

```json
{
  "mcpServers": {
    "persql": {
      "url": "https://mcp.persql.com",
      "headers": {
        "Authorization": "Bearer ${PERSQL_TOKEN}"
      }
    }
  }
}
```

The token is read from the `PERSQL_TOKEN` environment variable. Scope tokens narrowly: a token minted for one namespace cannot reach another.

## Pricing

PerSQL is usage-only. Five meters: requests, rows read, rows written, storage, AI tokens. No plans, no per-database fees, no seat fees. New accounts get a $5 welcome credit. Rates at [persql.com/pricing](https://persql.com/pricing).

## Links

- Product: https://persql.com
- Docs: https://docs.persql.com
- Console: https://console.persql.com
- MCP server: https://mcp.persql.com
- Support: admin@persql.com

## License

MIT
