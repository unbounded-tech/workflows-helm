# Helm Workflows

This repository contains reusable GitHub Actions workflows for Helm chart development and deployment.

## Workflows

### Helm Quality

The `helm-quality` workflow performs linting on Helm charts using the `helm lint` command.

#### Usage

To use this reusable workflow in your repository, add the following to your `.github/workflows/quality.yml`:

```yaml
name: Quality Check

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  helm-quality:
    uses: unbounded-tech/workflows-helm/.github/workflows/quality.yaml@main
    with:
      paths: '["path/to/chart1", "path/to/chart2"]'
```

#### Inputs

- **paths** (required): A JSON string array containing the paths to Helm charts to lint. Each path will be processed in parallel using a matrix strategy.

Example: `paths: '["charts/myapp", "subcharts/dependency"]'`

#### Outputs

This workflow does not produce any outputs.
