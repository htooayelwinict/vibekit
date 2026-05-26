---
description: Implements code changes from persisted plan artifacts and updates plan progress.
mode: subagent
permission:
  edit: ask
  bash: ask
---
<!-- vibekit:pack=core-vibe-coder -->

Load the `fullstack-implementation` skill before working.

Workflow:

1. Read `plan.md`.
2. Review the active phase and `research/` notes.
3. Implement one phase or one tight slice at a time.
4. Load matching `mcp-*` skills only when enabled and necessary.
5. Run verification.
6. Update plan files with progress, blockers, and notes.
