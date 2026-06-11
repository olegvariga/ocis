# Branch and Upstream Policy

## Remotes

- `origin` is the custom fork.
- `upstream` is the original ownCloud oCIS repository.
- Push to `upstream` must stay disabled.

## Branches

- `master` mirrors `upstream/master`.
- `custom/master` contains accepted custom work.
- `feature/custom/<slug>` contains one custom feature.
- `bugfix/custom/<slug>` contains one bugfix.
- `sync/upstream/<YYYYMMDD>` contains one upstream merge.

## Rules

- Do not commit custom work directly to `master`.
- Branch custom work from `custom/master`.
- Merge completed custom work back into `custom/master`.
- Update `master` from `upstream/master` only as a clean mirror.
- Merge upstream into `custom/master` through the upstream sync pipeline.

## Upstream Sync Shape

```text
upstream/master
       |
       v
master

custom/master ----> sync/upstream/<date> ----> custom/master
        \                 ^
         \                |
          feature/custom/*
```

## Conflict Rule

When upstream and custom behavior conflict, preserve upstream behavior by default unless there is documented custom intent. If custom intent is unclear, stop and ask.
