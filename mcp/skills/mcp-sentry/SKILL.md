---
name: mcp-sentry
description: Use when debugging production issues, stack traces, incidents, releases, or regressions using Sentry data.
---
<!-- vibekit:pack=mcp-sentry -->

# Sentry MCP

Use this skill when a task needs production error context from Sentry, including issues, stack traces, release impact, or recent regressions.

Only use this skill if the Sentry MCP tools are available in the current assistant. If they are not available, say that Sentry is not configured and continue with local evidence only.

## Workflow

1. Gather the relevant Sentry issue, project, or release context.
2. Identify the concrete error signal: stack trace, environment, release, frequency, or affected flow.
3. Correlate with recent deploys or versions when useful.
4. Confirm the root cause in the codebase before editing anything.
5. Summarize the evidence that links the production signal to the proposed fix.

## Good Uses

- Investigating production exceptions
- Checking whether a release introduced regressions
- Understanding real-world error frequency and impact

## Avoid

- Using Sentry for bugs that are fully reproducible locally without external context
- Treating Sentry symptoms as proof of root cause without code verification
