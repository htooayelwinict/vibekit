---
name: bugfix-and-debug
description: Diagnose failures, verify root cause, apply minimal fixes, and prevent regressions.
---
<!-- vibekit:pack=core-vibe-coder -->

# Bugfix And Debug

Use this skill for failing tests, crashes, exceptions, and unexpected behavior.

## Process

1. Capture the exact failure and reproduction path.
2. Form one to three ranked hypotheses.
3. If the bug needs external docs, browser evidence, GitHub context, or production incident data, load the matching `mcp-*` skill first.
4. Verify the most likely cause using code, logs, tests, and any relevant MCP evidence.
5. Make the smallest change that fixes the root cause.
6. Add or recommend a regression test.
7. Run the narrowest relevant verification first, then broader checks if available.

## Relevant MCP Skills

- `mcp-context7` for current framework or dependency behavior
- `mcp-playwright` for browser reproduction and UI validation
- `mcp-sentry` for production exceptions and release regressions
- `mcp-github` for linked issues, PR context, or CI failures

## Output

Report:

- Bug
- Root cause
- Fix
- Regression test
- Verification
