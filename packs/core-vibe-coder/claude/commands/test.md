---
description: Write, run, or fix tests with a TDD-minded workflow and optional browser validation when supported.
argument-hint: [test target or scope]
allowed-tools: Read, Edit, Write, Grep, Glob, Bash
---
<!-- vibekit:pack=core-vibe-coder -->

Use the testing-expert agent for: **$ARGUMENTS**

Workflow:

1. Identify the behavior to prove.
2. Add or adjust the narrowest useful test first when practical.
3. Run focused verification.
4. If browser behavior matters and Playwright MCP is enabled, use it.
5. If the failure pattern or test design is still unclear and Open Bridge is enabled, use it for a second-pass review.
6. Run broader relevant checks before completion.
