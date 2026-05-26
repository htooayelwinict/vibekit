---
description: Execute a persisted plan phase by phase and update repo plan artifacts as work progresses.
argument-hint: <plan-folder-path> [--phase <N>|--from <N>]
allowed-tools: Read, Edit, Write, Grep, Glob, Bash
---
<!-- vibekit:pack=core-vibe-coder -->

Use the fullstack-developer agent to implement: **$ARGUMENTS**

Workflow:

1. Read `plan.md` first.
2. Review the matching `research/` notes and phase files.
3. Implement the requested phase or next pending work in order.
4. Load a matching `mcp-*` skill only if the user already enabled that MCP and external context or second-opinion reasoning is actually needed.
5. Run focused verification, then broader checks.
6. Update phase status, notes, and blockers inside the plan folder.

Return:

- Active plan path
- Phase completed or updated
- Files changed
- Verification run
- Blockers or follow-ups
