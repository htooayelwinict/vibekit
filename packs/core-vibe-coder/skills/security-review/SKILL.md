---
name: security-review
description: Review changes for OWASP-minded security risks, secret handling, authorization gaps, and unsafe operational assumptions.
---
<!-- vibekit:pack=core-vibe-coder -->

# Security Review

Use this skill when the task is primarily a security audit or when a change touches auth, permissions, secrets, or data exposure.

## Workflow

1. Gather the relevant diff and runtime context.
2. Review authentication, authorization, input handling, output handling, and secrets.
3. Run available package or dependency audit commands when appropriate.
4. Use enabled MCP context only when it helps validate security-sensitive behavior or sanity-check a threat model on tricky code.
5. Report findings by severity with concrete remediation.

## Relevant MCP Skills

- `mcp-context7` for current security guidance in frameworks
- `mcp-github` for PR, issue, advisory, or workflow context
- `mcp-sentry` for security-relevant production failures
- `mcp-open-bridge` for second-pass threat modeling and focused review of suspicious logic or diffs

## Output

Report:

- Critical findings
- High-risk findings
- Improvements
- Verification or audit commands run
