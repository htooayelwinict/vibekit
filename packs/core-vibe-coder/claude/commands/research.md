---
description: Research a topic and save the findings into an existing plan folder or a standalone dated research folder.
argument-hint: <topic> [--plan <plan-folder>]
allowed-tools: Read, Write, Grep, Glob, Bash
---
<!-- vibekit:pack=core-vibe-coder -->

Use the researcher agent for: **$ARGUMENTS**

Workflow:

1. Define the question clearly.
2. Save findings under an existing plan's `research/` folder when one is provided.
3. Otherwise create `plan/research-<topic>-<timestamp>/`.
4. Use only supported, enabled `mcp-*` skills for external context.
5. Write a durable markdown note another agent can reuse later.

Return:

- Research question
- Saved path
- Summary
- Key findings
- Recommendation
