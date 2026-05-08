---
name: code-review-checklist
description: Review changes for correctness, security, regressions, maintainability, and missing tests.
---
<!-- vibekit:pack=core-vibe-coder -->

# Code Review Checklist

Use this skill for PR review, pre-merge checks, and quality audits.

## Priorities

1. Bugs and behavior regressions
2. Security and secret leakage
3. Missing or weak tests
4. Data loss and migration risk
5. Performance issues
6. Maintainability risks

## Relevant MCP Skills

- `mcp-github` for PR, issue, review, workflow, and release context
- `mcp-context7` for validating current external API usage against docs
- `mcp-playwright` for UI regression checks when visual behavior matters
- `mcp-sentry` for production-impact review when a fix targets live incidents
- `mcp-figma` for design fidelity checks on UI-heavy changes

## Output

Lead with findings ordered by severity. Include file references and concrete fixes. If no findings are found, say so and note residual risk.
