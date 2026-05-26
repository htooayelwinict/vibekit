<!-- vibekit:pack=core-vibe-coder -->
# /plan

Create a researched implementation plan with phases, risks, and verification.

## Arguments

- `request`: feature, refactor, migration, or risky change to plan.

## Workflow

1. Restate the goal and success criteria.
2. Search the repo for similar patterns, related tests, and constraints.
3. Identify concrete files, dependencies, and order of operations.
4. Load a matching `mcp-*` skill only if the user already enabled that MCP and external context or second-opinion reasoning is needed.
5. Create `plan/<topic>-<timestamp>/` with `README.md`, `plan.md`, `research/`, and `phases/`.
6. Break the work into small phases with risks, rollback notes, and verification.

## Escalation

Delegate to `planner` for substantial planning or unclear implementation paths.
