# Yet another repository of reusable workflows
[![Static Badge](https://img.shields.io/badge/GitHub%20Actions-reusable%20workflows-blue?logo=github)](https://docs.github.com/en/actions/using-workflows/reusing-workflows)
[![GitHub](https://img.shields.io/github/license/vbem/reusable?color=blue)](LICENSE)
[![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/vbem/reusable?label=Release&logo=github)](https://github.com/vbem/reusable/releases)
[![superlinter.test](https://github.com/vbem/reusable/actions/workflows/superlinter.test.yml/badge.svg)](https://github.com/vbem/reusable/actions/workflows/superlinter.test.yml)

## `superlinter`
[`superlinter.yml`](.github/workflows/superlinter.yml) predefines generic configurations for the well-known [*Super-Linter* action](https://github.com/marketplace/actions/super-linter). Create `.github/workflows/linter.yaml` in your repository:
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
    uses: vbem/reusable/.github/workflows/superlinter.yml@v1
...
```