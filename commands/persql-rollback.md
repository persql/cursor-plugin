---
name: persql-rollback
description: Roll the current PerSQL database back to a prior snapshot or point in time.
---

# Roll back a PerSQL database

1. List recent snapshots via the `list_snapshots` MCP tool. If none exist, fall back to `restore_to_time` with a timestamp from the user.
2. Confirm the target with the user before restoring:
   - Snapshot id (from `list_snapshots`), or
   - ISO 8601 timestamp within the namespace snapshot TTL.
3. Call `restore_snapshot` or `restore_to_time`. Report the new state to the user.
4. If the rollback is exploratory, claim a branch first with `claim_branch` and restore there instead. Do not restore the live database without explicit confirmation.
