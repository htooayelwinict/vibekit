---
name: mcp-github
description: Use when work depends on GitHub issues, pull requests, reviews, workflows, releases, or discussions beyond local git state.
---
<!-- vibekit:pack=mcp-github -->

# GitHub MCP

Use this skill when a task needs live GitHub state that local git does not provide, such as issue details, PR context, review comments, Actions runs, releases, or discussions.

Only use this skill if the GitHub MCP tools are available in the current assistant. If they are not available, say that GitHub MCP is not configured and continue with local git state only.

## Workflow

1. Pull the relevant GitHub context first.
2. Separate GitHub state from local repository state.
3. Use the external context to inform the coding, review, or planning task.
4. Keep GitHub write actions explicit; do not create or update remote resources unless the user asked.
5. Summarize the GitHub facts you relied on.

## Good Uses

- Reading issue or PR context before implementation
- Checking CI or workflow failures
- Reviewing comments, reviews, or release metadata

## Avoid

- Using GitHub MCP when plain local git already answers the question
- Making remote mutations without explicit user intent
