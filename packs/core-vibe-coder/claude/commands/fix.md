---
description: Diagnose and fix a bug with minimal targeted changes.
argument-hint: <bug-or-error>
allowed-tools: Read, Grep, Glob, Bash, Edit, Write
---
<!-- vibekit:pack=core-vibe-coder -->

Use the debugger agent for this issue: **$ARGUMENTS**

Work in this order:

- Capture the failure.
- Identify likely root causes.
- Verify the correct cause.
- Make the smallest fix.
- Add or recommend a regression test.
- Run relevant verification.
