---
name: fullstack-implementation
description: Implement planned work phase by phase using persistent repo artifacts, existing patterns, and verification.
---
<!-- vibekit:pack=core-vibe-coder -->

# Fullstack Implementation

Use this skill when the task is to implement code, not just plan or advise.

## Workflow

1. Read the active `plan.md` before editing code.
2. Review the matching `research/` notes and current phase file.
3. Follow existing repository patterns before introducing new structure.
4. If unfamiliar APIs, tricky behavior, or implementation trade-offs require external context or second-opinion reasoning and the user already enabled the MCP, load the matching `mcp-*` skill first.
5. Implement one phase or one tight slice at a time.
6. Run the narrowest relevant verification first, then broader checks.
7. Update plan artifacts so another assistant can resume work later.

## Required Plan-Aware Behavior

- Treat `plan/<topic>-<timestamp>/plan.md` as the execution source of truth.
- Update phase checklists or status markers when work completes.
- Record blockers, deviations, and follow-up work in the active phase file or `README.md`.
- If implementation reveals missing context, add it to `research/` instead of keeping it only in chat.

## Relevant MCP Skills

- `mcp-context7` for official framework or library docs
- `mcp-github` for PR, issue, workflow, or release context
- `mcp-figma` for design-driven implementation details
- `mcp-playwright` for browser verification and UI flows
- `mcp-sentry` for production issue context tied to the change
- `mcp-open-bridge` for implementation-option comparison, blocker analysis, and focused diff review

## Output

Report with:

- Active plan path
- Phase completed or updated
- Files changed
- Verification run
- Blockers or follow-ups
