---
description: Diagnose and fix a bug with minimal targeted changes and regression coverage.
argument-hint: <bug-or-error>
allowed-tools: Read, Grep, Glob, Bash, Edit, Write
---
<!-- vibekit:pack=core-vibe-coder -->

Use the debugger agent for this issue: **$ARGUMENTS**

Work in this order:

1. Capture the failure and reproduction path.
2. Form one to three likely root-cause hypotheses.
3. Verify the correct cause using code, logs, tests, and history.
4. Load a matching `mcp-*` skill only if the user already enabled that MCP and external context or a second-pass hypothesis check is actually needed.
5. Make the smallest fix that resolves the root cause.
6. Add or recommend regression coverage.
7. Run narrow verification first, then broader checks if available.

Return:

- Bug summary
- Reproduction or localization evidence
- Root cause
- Fix
- Regression coverage
- Verification
