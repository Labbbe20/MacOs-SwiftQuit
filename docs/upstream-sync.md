# Upstream sync

This fork is kept close to `onebadidea/swiftquit` by `.github/workflows/sync-upstream.yml`.

The workflow:

- runs daily at 03:37 UTC and can also be started manually from the Actions tab
- merges upstream `main` into this fork's `main`
- mirrors upstream tags into this fork, force-updating upstream tag names if they move
- creates or updates fork releases for each upstream release
- copies upstream release notes and release assets
- records upstream release metadata in `.github/upstream-sync/upstream-releases.json`, so asset changes with the same file size can still be detected on later runs
- updates `.github/upstream-sync/last-scheduled-run.txt` occasionally to reduce the chance that GitHub disables scheduled workflows in a quiet public fork

The workflow uses the repository `GITHUB_TOKEN` with `contents: write`.

If a run fails with `Resource not accessible by integration` or HTTP 403, enable read/write workflow token access under `Settings -> Actions -> General -> Workflow permissions`.
