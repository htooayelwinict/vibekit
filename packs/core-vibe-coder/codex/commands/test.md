<!-- vibekit:pack=core-vibe-coder -->
# /test

Design, add, or run focused tests for the requested behavior.

## Arguments

- `target`: feature, bug fix, file, command, or coverage concern.

## Workflow

1. Identify the behavior and smallest meaningful verification scope.
2. Prefer deterministic unit or integration coverage before broad end-to-end tests.
3. Add regression tests for bugs when practical.
4. Use browser validation for meaningful UI changes when available.
5. Run the narrowest relevant command first and report exact results.

## Escalation

Delegate to `testing-expert` for testing strategy or coverage work.
