# AGENTS.md

This repository uses a Codex framework stored in `.codex`.

Before doing repository work, read:

- `.codex/README.md`
- `.codex/framework.yaml`

For feature, bugfix, review, upstream sync, or release work, choose and follow the matching pipeline in `.codex/pipelines/`.

Keep durable Codex process logic, agent roles, templates, and policies inside `.codex`. Keep this file short as the repository-level bootstrap that Codex loads automatically.

Do not put custom feature commits on `master`. Use `custom/master` and `feature/custom/*`, `bugfix/custom/*`, or `sync/upstream/*` branches as defined in `.codex/framework.yaml`.
