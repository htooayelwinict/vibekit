<!-- vibekit:pack=core-vibe-coder -->
# /deploy

Plan or adjust deployment, CI/CD, Docker, runtime, or infrastructure workflows.

## Arguments

- `request`: deployment target, CI failure, Docker change, infrastructure task, or release concern.

## Workflow

1. Inspect existing scripts, workflows, Dockerfiles, deployment configs, and environment assumptions.
2. Identify credentials, production state, rollback, and permission risks.
3. Make minimal reproducible automation changes when implementation is requested.
4. Update setup or operations docs when behavior changes.
5. Verify with the narrowest safe local or CI command available.

## Escalation

Delegate to `devops-engineer` for infrastructure or automation-heavy work.
