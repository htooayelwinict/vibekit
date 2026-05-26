---
name: testing
description: Write, fix, and run tests using a TDD-minded workflow with optional browser validation through supported MCPs.
---
<!-- vibekit:pack=core-vibe-coder -->

# Testing

Use this skill for automated tests, coverage improvements, regression tests, and end-to-end or browser verification.

## Workflow

1. Identify the behavior to prove.
2. Prefer writing or updating the test before changing implementation when practical.
3. Run the narrowest relevant test first.
4. If browser behavior matters and the user enabled Playwright MCP, use `mcp-playwright`.
5. If the failure pattern or test design is still unclear and the user enabled Open Bridge, use `mcp-open-bridge` for a second-pass test or diagnosis review.
6. After the focused test passes, run broader relevant verification.

## Relevant MCP Skills

- `mcp-context7` for framework-specific testing APIs
- `mcp-playwright` for browser flows, snapshots, and UI checks
- `mcp-github` for CI failures or test-related PR context
- `mcp-open-bridge` for flaky-test hypothesis review and alternative regression-test ideas

## Output

Include:

- Tests added or updated
- Focused verification run
- Broader verification run
- Remaining gaps
