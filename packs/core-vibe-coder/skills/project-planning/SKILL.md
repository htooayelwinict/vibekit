---
name: project-planning
description: Create concise implementation plans with research, phases, risks, and verification.
---
<!-- vibekit:pack=core-vibe-coder -->

# Project Planning

Use this skill when a change needs structure before implementation.

## Process

1. Restate the goal in one sentence.
2. Search the codebase for existing patterns.
3. If the task needs external docs, GitHub state, browser checks, design context, or production incident data, load the matching `mcp-*` skill first.
4. Identify concrete files likely to change.
5. Break work into small phases.
6. List risks and rollback considerations.
7. Define verification commands.

## Relevant MCP Skills

- `mcp-context7` for official library and framework docs
- `mcp-github` for issues, PRs, CI, releases, and discussions
- `mcp-figma` for design-driven implementation planning
- `mcp-sentry` for production issue or release context
- `mcp-playwright` for browser-flow or UI verification planning

## Output

Return a plan with:

- Goal
- Existing patterns
- Files to change
- Phases
- Risks
- Verification
