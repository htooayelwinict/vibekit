---
description: Create a researched implementation plan with phases, risks, and verification.
agent: planner
subtask: true
---
<!-- vibekit:pack=core-vibe-coder -->

Create a structured implementation plan for: $ARGUMENTS

Process:

1. Restate the goal and success criteria.
2. Search the repo for similar patterns, related tests, and constraints.
3. Identify concrete files, dependencies, and order of operations.
4. Load a matching `mcp-*` skill only if the user already enabled that MCP and external context or second-opinion reasoning is actually needed.
5. Create a persistent `plan/<topic>-<timestamp>/` folder with `README.md`, `plan.md`, `research/`, and `phases/`.
6. Break the work into small phases with risks, rollback notes, and verification.

Return:

- Goal
- Acceptance criteria
- Existing patterns
- Files to change
- Phase plan
- Risks and unknowns
- Verification commands
- Recommended first implementation step
- Plan folder path
