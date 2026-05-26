---
description: Initialize, update, or summarize documentation so repo docs stay aligned with code and workflow artifacts.
argument-hint: <init|update|summarize> [target]
allowed-tools: Read, Edit, Write, Grep, Glob, Bash
---
<!-- vibekit:pack=core-vibe-coder -->

Use the project-manager agent for documentation work: **$ARGUMENTS**

Workflow:

1. Decide whether this is `init`, `update`, or `summarize`.
2. Identify the relevant docs and any linked plan artifacts.
3. Create missing docs if the repo does not have a stable docs structure yet.
4. Keep commands, paths, and examples accurate.
5. Report remaining stale docs if any.
