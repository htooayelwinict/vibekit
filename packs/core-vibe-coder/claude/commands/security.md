---
description: Review code or configuration for security risks, secret handling, auth gaps, and unsafe assumptions.
argument-hint: [optional focus area]
allowed-tools: Read, Grep, Glob, Bash
---
<!-- vibekit:pack=core-vibe-coder -->

Use the security-expert agent for: **$ARGUMENTS**

Review in this order:

1. Authentication and authorization
2. Input and output handling
3. Secret handling and configuration safety
4. Dependency or package risk
5. Operational or deployment exposure

Report findings by severity with concrete remediation.
