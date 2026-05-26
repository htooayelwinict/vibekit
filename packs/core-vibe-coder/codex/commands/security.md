<!-- vibekit:pack=core-vibe-coder -->
# /security

Review security-sensitive code, configuration, dependencies, or workflows.

## Arguments

- `target`: feature, auth flow, API, config, dependency, or diff to review.

## Workflow

1. Identify trust boundaries, secrets, sensitive data, and attacker-controlled inputs.
2. Inspect auth, authorization, validation, storage, logging, and dependency surfaces.
3. Prioritize exploitable issues and concrete mitigations.
4. Never write secrets into tracked files.
5. Recommend targeted verification such as tests, secret scans, or config checks.

## Escalation

Delegate to `security-expert` for security audits or risky changes.
