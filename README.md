# Yet another repository of reusable workflows

[![Static Badge](https://img.shields.io/badge/GitHub%20Actions-reusable%20workflows-blue?logo=github)](https://docs.github.com/en/actions/using-workflows/reusing-workflows)
[![GitHub](https://img.shields.io/github/license/kugelbit-com/reusable?color=blue)](LICENSE)
[![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/kugelbit-com/reusable?label=Release&logo=github)](https://github.com/kugelbit-com/reusable/releases)
[![superlinter.test](https://github.com/kugelbit-com/reusable/actions/workflows/superlinter.test.yml/badge.svg)](https://github.com/kugelbit-com/reusable/actions/workflows/superlinter.test.yml)
[![keepalive.test](https://github.com/kugelbit-com/reusable/actions/workflows/keepalive.test.yml/badge.svg)](https://github.com/kugelbit-com/reusable/actions/workflows/keepalive.test.yml)

## `superlinter`

Forked from https://github.com/vbem/reusable

[`superlinter.yml`](.github/workflows/superlinter.yml) predefined generic configurations for the well-known [*Super-Linter* action](https://github.com/marketplace/actions/super-linter). Create `.github/workflows/linter.yaml` in your repository:

```yaml
---
name: Linter

concurrency:
  group: ${{ github.workflow }}@${{ github.ref }}
  cancel-in-progress: true

on:
  push:
    branches: [master, main]
  workflow_dispatch:

jobs:
  calling:
    permissions:
      contents: read
      packages: read
      statuses: write
    uses: kugelbit-com/reusable/.github/workflows/superlinter.yml@v1
...
```

## `keepalive`

[`keepalive.yml`](.github/workflows/keepalive.yml) is a wrapper the well-known [*Keepalive Workflow* action](https://github.com/marketplace/actions/keepalive-workflow). Create `.github/workflows/alive.yaml` in your repository:

```yaml
---
name: Alive

on:
  schedule: [ cron: '0 0 * * 1,3,5' ] # in UTC-0 timezone
  workflow_dispatch:

jobs:
  calling:
    permissions:
      contents: write
    uses: kugelbit-com/reusable/.github/workflows/keepalive.yml@v1
...
```
