# SCANOSS GitHub Action Usage Example

This repository serves as an example to demonstrate how to use the [SCANOSS GitHub Action](https://github.com/scanoss/actions-scan/) for license management in your projects. SCANOSS provides two predefined policies for scanning: `copyleft` and `undeclared`.

## Overview

The repository is structured into two branches to showcase different scenarios:

- [`main`](https://github.com/scanoss/integration-github-actions/tree/main): Demonstrates a scenario where the codebase comply with the policies:
    - No copyleft licenses are found within the codebase.
    - All components are correctly declared in the [`sbom.json`](sbom.json) file. 


- [`policy/violations`](https://github.com/scanoss/integration-github-actions/tree/policy/violations): Illustrates the case where the codebase does not comply with the policies. You can find the failing PR [here](https://github.com/scanoss/integration-github-actions/pull/14).
    - Introduction of copyleft licenses.
    - Usage of components that are not declared in the `sbom.json`. 
  

## Policies in Detail

- **Copyleft**: This policy scans your code for copyleft licenses. If no copyleft licenses are identified, the check passes. Otherwise, it fails, indicating non-compliance.
- **Undeclared**: Requires the explicit declaration of all utilized components within a `sbom.json` file. Failure to declare any component results in a failed check, highlighting undeclared usage.

## How to Use This Action in Your Project

To use the SCANOSS GitHub Action in your project, you can add a workflow file under `.github/workflows` with the following basic setup:

```yaml
name: Example SCANOSS Action

on:
  pull_request:
    branches:
      - main
  push:
    branches:
      - main

permissions:
  contents: read
  pull-requests: write
  checks: write

jobs:
  scanoss-analysis:
    name: SCANOSS Analysis
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        id: checkout
        uses: actions/checkout@v4

      - name: Run SCANOSS analysis
        id: scan
        uses: scanoss/actions-scan@main
        with:
          policies: copyleft, undeclared
```
