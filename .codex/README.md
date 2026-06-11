# Codex Custom Development Framework

This directory contains the full operating framework for developing custom oCIS features with Codex agents while keeping the upstream core mergeable.

The repository code may change outside `.codex` when a feature is implemented. The development rules, pipeline definitions, agent roles, templates, and process documentation must stay inside `.codex`.

## Goals

- Keep `master` aligned with `upstream/master`.
- Develop custom work on isolated branches and integrate through `custom/master`.
- Prefer extension, configuration, adapter, or service boundaries before changing oCIS core files.
- Make every Codex run reproducible through a pipeline YAML, an input brief, and saved output artifacts.
- Use tests and review gates before any custom feature reaches `custom/master`.

## Directory Map

- `.codex/framework.yaml` - framework registry and default policies.
- `.codex/pipelines/` - YAML pipelines Codex should execute.
- `.codex/agents/` - role prompts and responsibilities for Codex agents.
- `.codex/templates/` - input and output document templates.
- `.codex/docs/` - architecture, branch policy, testing, and bugfix playbooks.
- `.codex/runs/` - local run artifacts created during pipeline execution.

## Standard Invocation

Ask Codex to run a pipeline by naming the YAML file and providing an input brief.

Example:

```text
Codex, run .codex/pipelines/feature-development.yaml.
Use this feature brief:
<paste completed .codex/templates/feature-spec.md>
```

Codex must read `.codex/framework.yaml`, then the selected pipeline YAML, then the referenced agent files and templates.

## Default Branch Model

- `master` is a clean mirror of `upstream/master`.
- `custom/master` is the integration branch for custom features.
- `feature/custom/<slug>` is used for new custom features.
- `bugfix/custom/<slug>` is used for bugs in custom features.
- `sync/upstream/<YYYYMMDD>` is used for upstream merge work.

## First Setup Commands

These commands are documented here for humans and Codex. Run them only when the branch does not already exist.

```bash
git checkout master
git fetch upstream
git switch -c custom/master
git push -u origin custom/master
```

After that, all custom feature work should branch from `custom/master`, not from `master`.
