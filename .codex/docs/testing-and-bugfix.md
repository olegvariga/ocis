# Testing and Bugfix Strategy

Testing should match the risk of the change. Start with the smallest meaningful check, then expand when behavior is shared or core-adjacent.

## Test Levels

- Unit: package-level behavior.
- Integration: service boundary, storage, auth, API, or workflow behavior.
- Regression: a previously failing case.
- Smoke: basic runtime or operational sanity check.
- Manual: accepted only when automation is unavailable and steps are documented.

## Feature Test Rule

Every custom feature should have one of:

- an automated test that proves acceptance criteria
- a smoke check with deterministic steps
- a written reason why automation is not feasible yet

## Bugfix Test Rule

Every bugfix should include:

- reproduction evidence
- fix evidence
- regression test or documented manual regression check

## Upstream Sync Test Rule

Every upstream sync should include:

- targeted tests for conflict areas
- custom feature regression checks
- skipped broad checks with reasons

## Test Report Requirements

Use `.codex/templates/test-report.md` and include:

- exact commands
- pass/fail status
- behavior covered
- skipped checks
- remaining risk

## When Tests Fail

Codex should:

1. Record the failing command.
2. Identify whether the failure is custom, upstream, environment, or test-only.
3. If custom, switch to `.codex/pipelines/bugfix.yaml`.
4. If upstream or environment, document evidence and stop for decision.
