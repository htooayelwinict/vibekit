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

## Review Workflow

1. Gather the relevant diff, files, and surrounding context.
2. Review for correctness, regressions, security, data safety, testing gaps, and maintainability.
3. If review quality depends on GitHub context, external docs, browser verification, production incident data, design references, or a second-pass reasoning check on a tricky change and the user already enabled the MCP, load the matching `mcp-*` skill first.
4. Verify claims where possible instead of guessing.
5. Report findings ordered by severity with concrete remediation.
6. If no findings are present, say so explicitly and note residual risks or testing gaps.

## Review Checklist

- Correctness and edge cases
- Input validation, authorization, and secret handling
- Data safety, migrations, and rollback concerns
- Test coverage and verification gaps
- Performance, duplication, and maintainability
- User-facing regressions, accessibility, and documentation drift

## Relevant MCP Skills

- `mcp-github` for PR, issue, review, workflow, and release context
- `mcp-context7` for validating current external API usage against docs
- `mcp-playwright` for UI regression checks when visual behavior matters
- `mcp-sentry` for production-impact review when a fix targets live incidents
- `mcp-figma` for design fidelity checks on UI-heavy changes
- `mcp-open-bridge` for adversarial review of risky diffs and second-pass reasoning on edge cases

## Output

Lead with findings ordered by severity. Include file references and concrete fixes. If no findings are found, say so and note residual risk.

Use [reference.md](reference.md) for severity cues, common finding types, and review prompts.
