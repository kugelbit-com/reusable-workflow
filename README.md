# Yet another repository of reusable workflows for GitHub Actions
[![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/vbem/reusable?label=Release&logo=github)](https://github.com/vbem/reusable/releases)
[![Test linter-default](https://github.com/vbem/reusable/actions/workflows/linter-default.test.yml/badge.svg)](https://github.com/vbem/reusable/actions/workflows/linter-default.test.yml)

## Super-Linter

### Default Pattern

Create `.github/workflows/linter.yaml` in your repository:
```yaml
---
name: Super Linter

concurrency:
  group: ${{ github.workflow }}@${{ github.ref }}
  cancel-in-progress: true

on:
  push:
    branches: [master, main]
  workflow_dispatch:

jobs:
  calling:
    uses: vbem/reusable/.github/workflows/linter-default.yml@v1
...
```