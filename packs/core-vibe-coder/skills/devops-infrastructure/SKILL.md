---
name: devops-infrastructure
description: Manage deployment, Docker, CI/CD, environment, and infrastructure changes with rollback and secret-safety requirements.
---
<!-- vibekit:pack=core-vibe-coder -->

# DevOps Infrastructure

Use this skill when the work is about deployment, automation, runtime config, or infrastructure safety rather than application feature code.

## Workflow

1. Inspect current infrastructure files and deployment assumptions.
2. Document the desired change and rollback path before editing.
3. Keep secrets out of tracked files and prefer environment-based configuration.
4. If rollout trade-offs, config behavior, or incident context remain unclear and the user enabled a relevant MCP, load the matching `mcp-*` skill before editing.
5. Validate configs with the narrowest available checks before broader rollout steps.
6. Record post-change verification and rollback notes.

## Relevant MCP Skills

- `mcp-context7` for current tool and platform docs
- `mcp-github` for workflow, action, and release context
- `mcp-sentry` for production release and incident validation
- `mcp-open-bridge` for rollout-option comparison, incident synthesis, and config review

## Output

Return:

- Infrastructure goal
- Files changed
- Rollback plan
- Verification run
