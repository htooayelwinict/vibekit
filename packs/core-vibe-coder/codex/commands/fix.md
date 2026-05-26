<!-- vibekit:pack=core-vibe-coder -->
# /fix

Debug and fix a failure, regression, crash, or failing test.

## Arguments

- `issue`: symptom, command output, failing test, or bug report.

## Workflow

1. Reproduce or tightly describe the failure.
2. Inspect nearby code, logs, tests, and recent changes.
3. Identify the root cause before editing.
4. Apply the smallest safe fix.
5. Add regression coverage when practical.
6. Run targeted verification.

## Escalation

Delegate to `debugger` when root-cause analysis is non-trivial.
