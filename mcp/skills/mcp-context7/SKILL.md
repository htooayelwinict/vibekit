---
name: mcp-context7
description: Use when a task needs current official library or framework documentation beyond what the repo already shows.
---
<!-- vibekit:pack=mcp-context7 -->

# Context7 MCP

Use this skill when a task depends on exact API behavior, current framework docs, config keys, migration steps, or authoritative usage examples.

Only use this skill if the Context7 MCP tools are available in the current assistant. If they are not available, say that Context7 is not configured and continue with repo-local context.

## Workflow

1. Resolve the target library or framework first.
2. Query only the specific API, pattern, or migration detail needed for the task.
3. Prefer official docs and exact examples over memory.
4. Summarize the relevant finding briefly and apply it to the codebase task.

## Good Uses

- Verifying framework APIs before coding
- Checking exact config syntax or CLI flags
- Looking up current docs for dependencies used in this repo

## Avoid

- Using Context7 for questions the local codebase already answers
- Dumping long doc excerpts into the response
