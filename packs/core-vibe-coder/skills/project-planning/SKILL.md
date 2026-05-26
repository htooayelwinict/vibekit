---
name: project-planning
description: Create structured implementation plans with repository research, phased execution, risks, and verification.
---
<!-- vibekit:pack=core-vibe-coder -->

# Project Planning

Use this skill when work is unclear, spans multiple files, carries hidden risk, or benefits from sequencing before implementation.

## Workflow

1. Restate the goal in one sentence.
2. Search the codebase for existing patterns, related tests, and constraints.
3. If the task needs external docs, GitHub state, browser checks, design context, production incident data, or a second-opinion reasoning pass and the user already enabled the MCP, load the matching `mcp-*` skill first.
4. Identify concrete files, dependencies, and likely order of operations.
5. Break the work into small phases that can be verified independently.
6. List risks, rollback considerations, assumptions, and unknowns.
7. Define exact verification commands based on the repository.
8. Always write durable plan artifacts inside the repository so later implementation can reload context without relying on chat history.

## Planning Checklist

- Goal and acceptance criteria
- Existing patterns to follow
- Files likely to change
- Dependencies and sequencing
- Risks and rollback notes
- Verification commands

## Phase Heuristics

- Put data shape, schema, or contract changes before consumers.
- Put shared types, helpers, or interfaces before dependent files.
- Prefer phases that can be reviewed and verified independently.
- Call out anything that should ship behind a flag or be rollout-safe.

## Relevant MCP Skills

- `mcp-context7` for official library and framework docs
- `mcp-github` for issues, PRs, CI, releases, and discussions
- `mcp-figma` for design-driven implementation planning
- `mcp-sentry` for production issue or release context
- `mcp-playwright` for browser-flow or UI verification planning
- `mcp-open-bridge` for architecture comparison, plan stress-testing, and second-pass reasoning

## Required Plan Artifacts

Create a folder using this structure:

```text
plan/
└── <topic>-<YYYYMMDD-HHMMSS>/
    ├── README.md
    ├── plan.md
    ├── research/
    │   ├── requirements.md
    │   ├── existing-code.md
    │   └── references.md
    └── phases/
        ├── phase-1-<name>.md
        ├── phase-2-<name>.md
        └── ...
```

Rules:

- `plan.md` is the single source of truth for implementation.
- `README.md` is the quick human summary.
- `research/` captures inputs, existing patterns, and external references.
- `phases/` contains execution-ready steps with verification.

## Output

Return a plan with these sections:

- Goal
- Acceptance criteria
- Existing patterns
- Files to change
- Phases
- Risks and unknowns
- Verification
- Recommended first implementation step

Use [reference.md](reference.md) for reusable templates, estimation cues, and risk prompts.
