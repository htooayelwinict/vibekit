---
description: Brainstorm options, trade-offs, and recommendations without implementing code, then save a durable summary.
argument-hint: <topic> [--plan <plan-folder>]
allowed-tools: Read, Write, Grep, Glob, Bash
---
<!-- vibekit:pack=core-vibe-coder -->

Use the brainstormer agent for: **$ARGUMENTS**

Rules:

- Advise only; do not implement.
- Save the outcome under an active plan's `research/` folder when relevant.
- Otherwise create `brainstorm/<topic>-<timestamp>.md`.

Return:

- Problem statement
- Options considered
- Recommended path
- Risks and mitigations
- Saved path
