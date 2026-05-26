<!-- vibekit:pack=core-vibe-coder -->
# Project Planning Reference

## Required Plan Folder

```text
plan/
└── <topic>-<YYYYMMDD-HHMMSS>/
    ├── README.md
    ├── plan.md
    ├── research/
    │   ├── requirements.md
    │   ├── existing-code.md
    │   └── references.md
    └── phases/
        ├── phase-1-<name>.md
        ├── phase-2-<name>.md
        └── ...
```

`plan.md` should summarize the full execution path so implementation agents can resume from it later.

## Phase Template

```markdown
## Phase N: [Name]

### Objective
[What this phase accomplishes]

### Tasks
- [ ] Task with `path/to/file`

### Files
| File | Action | Notes |
|------|--------|-------|
| `path/to/file` | Create/Modify/Delete | Why it changes |

### Risks
- [Risk and mitigation]

### Verification
```bash
[commands]
```
```

## Estimation Cues

| Size | Typical Scope |
|------|---------------|
| XS | Single file or tiny follow-up |
| S | A few related files in one layer |
| M | Several files across one workflow |
| L | Cross-cutting work with meaningful risk |
| XL | Multi-step feature or migration-heavy change |

## Risk Prompts

- Could this break existing data, contracts, permissions, or user flows?
- Does the change require ordering or rollback planning?
- Are there hidden dependencies such as config, background jobs, migrations, or browser flows?
- Should rollout be guarded, staged, or manually checked?

## Verification Prompts

- What is the narrowest command that proves the first phase works?
- Which broader test, lint, type, or build checks are relevant before completion?
- Are there manual verification steps that need to be recorded explicitly?

## plan.md Template

```markdown
# Plan: [Topic]

## Context
[What we are building and why]

## Acceptance Criteria
- [ ] Criterion 1

## Existing Patterns
- `path/to/file` — pattern to follow

## Phase Overview
| # | Phase | Objective | Verification |
|---|-------|-----------|--------------|
| 1 | ... | ... | ... |

---

## Phase 1: [Name]
### Objective
[Goal]

### Tasks
- [ ] Task with `path/to/file`

### Files
| File | Action | Notes |
|------|--------|-------|

### Verification
```bash
[commands]
```

---

## Risks
- [Risk and mitigation]
```
