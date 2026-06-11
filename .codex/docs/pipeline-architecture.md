# Pipeline Architecture

The framework is built around explicit pipeline YAML files and role-specific Codex agents.

## Control Flow

```text
User request
  -> pipeline YAML
  -> framework registry
  -> agent role files
  -> source inspection
  -> ordered stages
  -> gates
  -> final report
```

## Data Flow

```text
Input template
  -> plan artifact
  -> architecture or diagnosis artifact
  -> implementation or resolution notes
  -> review report
  -> test report
  -> merge or hold decision
```

## Pipeline Responsibilities

Pipelines define:

- required inputs
- branch rules
- agent sequence
- expected artifacts
- mandatory gates
- stop conditions
- failure policy

Agents define:

- role responsibility
- operating rules
- output format

Docs define:

- stable project policy
- merge strategy
- testing strategy
- bugfix strategy

## Why This Exists

oCIS is a large upstream project. Custom features must be developed in a way that avoids unnecessary core drift. The framework makes Codex produce the same kinds of decisions each time: plan, boundary choice, implementation, review, tests, and upstream merge readiness.

## No Hidden Runner

There is no required executable runner in this initial version. The YAML files are the source of truth for Codex-managed work. A future runner can be added under `.codex/` if repeated manual steps become expensive.
