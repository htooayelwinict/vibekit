---
name: mcp-playwright
description: Use when you need browser reproduction, UI inspection, screenshots, or flow verification in a running app.
---
<!-- vibekit:pack=mcp-playwright -->

# Playwright MCP

Use this skill for browser-based debugging, UI verification, end-to-end flow checks, and screenshot capture.

Only use this skill if the Playwright MCP tools are available in the current assistant. If they are not available, say that Playwright is not configured and continue with non-browser investigation.

## Workflow

1. Open the relevant page or flow.
2. Reproduce the bug or inspect the target state.
3. Capture screenshots when the visual result matters.
4. Check mobile and desktop layouts when the issue is responsive or UI-heavy.
5. Report concrete browser observations before proposing code changes.

## Good Uses

- Reproducing UI bugs
- Verifying forms, navigation, and flows
- Checking responsive layout regressions
- Confirming the result after a frontend change

## Avoid

- Using browser tooling for purely backend or static code questions
- Performing destructive actions unless the user explicitly asked for them
