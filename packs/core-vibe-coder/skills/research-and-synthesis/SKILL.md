---
name: research-and-synthesis
description: Gather durable research notes from repo context and supported MCPs, then save them where later work can reuse them.
---
<!-- vibekit:pack=core-vibe-coder -->

# Research And Synthesis

Use this skill when a task needs external documentation, comparisons, release context, design references, or durable supporting notes.

## Workflow

1. Define the research question clearly.
2. Decide where the notes belong:
   - existing plan: `plan/<topic>/research/`
   - standalone research: `plan/research-<topic>-<timestamp>/`
3. Use supported MCP skills only when the user has enabled them, including `mcp-open-bridge` when a second-pass synthesis or option comparison would help.
4. Prefer official docs, maintainers, and primary-source project context over random commentary.
5. Write the findings into repo files so planning and implementation can reload them later.

## Relevant MCP Skills

- `mcp-context7` for official library and framework documentation
- `mcp-github` for issues, PRs, releases, and workflow context
- `mcp-figma` for design specifications and component intent
- `mcp-sentry` for production errors, releases, and incident context
- `mcp-playwright` for live browser evidence when behavior must be observed directly
- `mcp-open-bridge` for second-opinion synthesis, batch comparison, and focused file analysis

## If External Context Is Unavailable

- Say which relevant MCP is missing or not enabled.
- Continue with repo-local research and clearly label the gap.
- Do not pretend unsupported web-search MCPs are available.

## Output

Save a markdown note that includes:

- Question
- Summary
- Key findings
- Recommendation
- References or source pointers
- Saved path
