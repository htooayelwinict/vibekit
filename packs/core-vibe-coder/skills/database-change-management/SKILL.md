---
name: database-change-management
description: Plan and implement safe schema, relationship, index, and backfill changes with rollback awareness.
---
<!-- vibekit:pack=core-vibe-coder -->

# Database Change Management

Use this skill when work touches schema, migrations, indexes, query behavior, or data-shape contracts.

## Workflow

1. Audit current schema usage, models, and dependent code.
2. Prefer additive and reversible changes first.
3. Document migration order, rollback expectations, and any backfill requirements.
4. Update related models, queries, and tests.
5. If migration patterns, rollout decisions, or incident context need extra context and the user enabled a relevant MCP, load the matching `mcp-*` skill first.
6. Validate with the repo's migration and verification commands when available.

## Rules

- Avoid destructive changes without an explicit rollback or data-preservation plan.
- Prefer nullable or defaulted additions for existing tables.
- Record deployment notes when migration sequencing matters.

## Relevant MCP Skills

- `mcp-context7` for migration, ORM, and database-tool documentation
- `mcp-github` for migration-related PR, issue, or workflow context
- `mcp-sentry` for production failures tied to schema or query regressions
- `mcp-open-bridge` for sequencing review, rollback trade-offs, and tricky query or schema analysis

## Output

Report:

- Schema or data change
- Files updated
- Rollback or deployment notes
- Verification run
