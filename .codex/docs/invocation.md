# Codex Pipeline Invocation

Codex pipelines in this repository are YAML operating contracts, not GitHub Actions workflows. A human starts a pipeline by asking Codex to run one of the files in `.codex/pipelines`.

## Invocation Pattern

```text
Codex, run .codex/pipelines/<pipeline>.yaml.
Use this input:
<paste completed template>
```

Codex should then:

1. Read `.codex/framework.yaml`.
2. Read the selected pipeline YAML.
3. Read referenced agent files from `.codex/agents`.
4. Read referenced templates and docs.
5. Inspect repository state.
6. Execute the pipeline stages in order.
7. Save run artifacts under `.codex/runs/<run-id>/`.
8. Report changed files, tests, risks, and next step.

## Pipeline Selection

- New custom feature: `.codex/pipelines/feature-development.yaml`
- Bug in custom behavior: `.codex/pipelines/bugfix.yaml`
- Independent review: `.codex/pipelines/review-gate.yaml`
- Merge upstream changes: `.codex/pipelines/upstream-sync.yaml`
- Validate a release candidate: `.codex/pipelines/release-candidate.yaml`

## Run IDs

Use this format:

```text
YYYYMMDD-HHMM-<pipeline>-<slug>
```

Example:

```text
.codex/runs/20260610-1420-feature-login-policy/
```

## Human Approval Points

Codex must stop and ask before:

- direct core changes without documented justification
- risky conflict resolution during upstream sync
- destructive Git operations
- broad dependency or toolchain changes
- behavior that changes upstream semantics unexpectedly
