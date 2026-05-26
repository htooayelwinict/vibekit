---
name: documentation-management
description: Initialize, update, and maintain durable project documentation that stays aligned with the codebase and workflow artifacts.
---
<!-- vibekit:pack=core-vibe-coder -->

# Documentation Management

Use this skill when code, setup, workflows, or project structure changes need to be reflected in docs.

## Workflow

1. Determine whether the task is `init`, `update`, or `summarize`.
2. Identify which docs are the source of truth in this repo.
3. If the repo lacks docs, create a minimal structure under `docs/`.
4. Keep file paths, commands, and examples accurate.
5. If external product, API, design, rollout, or synthesis context would improve the docs and the user enabled a relevant MCP, load the matching `mcp-*` skill first.
6. Cross-check plan artifacts if implementation changed the agreed approach.

## Recommended Minimal Docs

- `README.md`
- `docs/project-overview.md`
- `docs/codebase-summary.md`
- `docs/code-standards.md`
- `docs/system-architecture.md`

## Relevant MCP Skills

- `mcp-context7` for exact external API or framework references
- `mcp-github` for issue, PR, release, or workflow details that docs should reflect
- `mcp-figma` for UI or design-system documentation inputs
- `mcp-sentry` for incident or release context that changes operational docs
- `mcp-open-bridge` for summarizing complex findings into durable docs

## Output

Report:

- Docs created or updated
- Why they changed
- Any stale docs still needing work
