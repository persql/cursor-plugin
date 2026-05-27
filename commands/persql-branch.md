---
name: persql-branch
description: Claim a fresh PerSQL branch with a scoped token and report the connection details.
---

# Claim a PerSQL branch

1. Call the `claim_branch` MCP tool with `purpose` describing why the branch is needed and `ttlSec` (default 3600).
2. Capture the returned `branchRef` and scoped `token`.
3. Print the connection snippet:
   ```
   Branch: <branchRef>
   Token:  <token>  (expires in <ttlSec>s)
   ```
4. Note that the branch will auto-delete on TTL expiry; the caller can delete it earlier with `delete_branch`.
