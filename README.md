# SCANOSS GitHub Action Usage Example


This repository serves as an example to demonstrate how to consume the [SCANOSS Github Action](https://github.com/scanoss/actions-scan/) for license management in your projects.
SCANOSS offers two predefined policies for scanning licenses: `copyleft` and `undeclared`.

## Supported Policies

- **Copyleft**: Scans your code for copyleft licenses. If no copyleft licenses are found, the workflow passes. Otherwise, it fails.
- **Undeclared**: Requires the user to create a *sbom.json* file declaring all the components being used. If any component not declared in the sbom.json is detected, the workflow will fail.

## Repository Structure

This repository is organized into different branches to illustrate various use cases:

- [`policy/copyleft/no-copyleft`](https://github.com/scanoss/integration-test/tree/policy/copyleft/no-copyleft): Contains an example where no copyleft licenses are found.
- [`policy/copyleft/with-copyleft`](https://github.com/scanoss/integration-test/tree/policy/copyleft/with-copyleft): Contains an example where copyleft licenses are detected.
- `policy/undeclared/no-undeclared-components`: Contains an example without undeclared components.
- `policy/undeclared/with-undeclared-components`: Contains an example with undeclared components.


## Examples in Action
To illustrate how these policies work in real scenarios, we suggest reviewing the Pull Requests in this repository. We will keep PRs open for each use case:

- [PR for no-copyleft](https://github.com/scanoss/integration-test/pull/10)
- [PR for with-copyleft](https://github.com/scanoss/integration-test/pull/9)
- PR for no-undeclared-components
- PR for with-undeclared-components

Each PR is associated with its respective use case branch and contains a workflow demonstrating the use of the corresponding policy.

