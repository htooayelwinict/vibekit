---
name: project-orchestration
description: Coordinate specialist agents, maintain handoffs, and keep durable progress artifacts updated.
---
<!-- vibekit:pack=core-vibe-coder -->

# Project Orchestration

Use this skill when the work spans multiple specialties or when coordination and status tracking matter as much as implementation.

## Workflow

1. Identify the domains involved.
2. Decide which specialist should handle each slice.
3. Keep scope, dependencies, and blockers visible.
4. If a handoff depends on external context or a second-opinion synthesis and the user enabled a relevant MCP, load the matching `mcp-*` skill first.
5. Update plan files, progress notes, or docs as handoffs happen.
6. Do not let important context live only in chat.

## Specialist Roster

- `planner`
- `fullstack-developer`
- `project-manager`
- `researcher`
- `brainstormer`
- `debugger`
- `reviewer`
- `testing-expert`
- `security-expert`
- `database-admin`
- `ui-ux-designer`
- `devops-engineer`

## Durable Coordination Artifacts

- active plan `README.md`
- active `plan.md`
- phase files under `phases/`
- research notes under `research/`
- docs updates when behavior or setup changes

## Relevant MCP Skills

- `mcp-context7` for external technical constraints that affect sequencing
- `mcp-github` for issue, PR, release, or workflow context during handoff
- `mcp-figma` for design dependencies that affect implementation routing
- `mcp-sentry` for live-incident pressure that changes priorities
- `mcp-playwright` for browser evidence that blocks or confirms a handoff
- `mcp-open-bridge` for synthesizing multi-source context into a cleaner execution path

## Output

Return:

- Scope
- Task breakdown
- Suggested agent routing
- Dependencies
- Blockers
- Files or notes updated
