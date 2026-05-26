---
description: Review current changes for bugs, security, regressions, maintainability, and missing tests.
agent: reviewer
subtask: true
---
<!-- vibekit:pack=core-vibe-coder -->

Review the current working tree. Focus: $ARGUMENTS

Review in this order:

1. Correctness and behavior regressions
2. Security and data safety
3. Missing or weak tests
4. Performance and maintainability risks
5. Verification gaps

Load a matching `mcp-*` skill only if the user already enabled that MCP and external context or a second-pass reasoning check is actually needed.

Report concrete findings first, ordered by severity, with file references and remediation. If no findings are present, say so explicitly and note any residual risks or testing gaps.
