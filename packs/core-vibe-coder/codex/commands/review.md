<!-- vibekit:pack=core-vibe-coder -->
# /review

Review changes for bugs, regressions, security issues, and missing tests.

## Arguments

- `target`: diff, branch, PR, file, or feature area to review.

## Workflow

1. Inspect the intended behavior and relevant diff.
2. Prioritize concrete defects over style preferences.
3. Check edge cases, auth boundaries, data handling, backwards compatibility, and tests.
4. Lead with findings ordered by severity, including exact file references.
5. If no findings are found, state that and name residual risks.

## Escalation

Delegate to `reviewer` for substantial code review.
