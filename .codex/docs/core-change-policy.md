# Core Change Policy

The default position is to avoid direct oCIS core changes.

## Preferred Boundaries

Use this order:

1. Configuration
2. Existing extension point
3. Adapter around existing behavior
4. Separate service or sidecar
5. Narrow core hook
6. Direct core change

## Direct Core Change Requirements

A direct core change must include:

- why configuration or extension was insufficient
- files touched
- expected upstream conflict risk
- rollback strategy
- focused regression tests
- review approval

## Core Risk Ratings

Low:

- isolated custom package
- config-only behavior
- no shared API change

Medium:

- adapter around shared behavior
- new hook
- existing tests need updates

High:

- direct changes in upstream-owned core packages
- behavior change for existing public API
- storage, auth, permissions, sharing, migration, or security-sensitive code

## Codex Stop Conditions

Codex must stop before continuing when:

- the plan requires a direct core change but no justification exists
- the change alters security or permission behavior without explicit acceptance criteria
- upstream behavior and custom behavior conflict without a documented decision
