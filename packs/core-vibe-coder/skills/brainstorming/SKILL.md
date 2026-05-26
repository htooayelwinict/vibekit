---
name: brainstorming
description: Explore options, trade-offs, and decision paths without implementing code, then save the result as a durable repo artifact.
---
<!-- vibekit:pack=core-vibe-coder -->

# Brainstorming

Use this skill when multiple approaches are plausible and the goal is to think clearly before committing.

## Rules

- Advise and compare; do not implement.
- Challenge assumptions kindly and concretely.
- Ground recommendations in the codebase, constraints, and supported context sources.

## Workflow

1. Frame the problem, goals, and constraints.
2. Gather relevant codebase patterns and any enabled MCP context, especially `mcp-open-bridge` when an extra option-comparison pass would help.
3. Generate multiple approaches.
4. Compare them by feasibility, effort, maintainability, risk, and fit with current architecture.
5. Recommend a path and write a durable summary.

## Saved Output

- If tied to an active plan, save under `plan/<topic>/research/brainstorm-<subject>.md`.
- Otherwise save under `brainstorm/<subject>-<timestamp>.md`.

## Relevant MCP Skills

- `mcp-context7` for current library patterns
- `mcp-github` for issue, PR, or release context
- `mcp-figma` for product and design constraints
- `mcp-sentry` for production pain points influencing trade-offs
- `mcp-open-bridge` for extra ideation, trade-off comparison, and synthesis across options

## Output

Include:

- Problem statement
- Constraints
- Evaluated options
- Recommended path
- Risks and mitigations
- Next steps
- Saved path
