# GAWG Release Action

This GitHub Action generates a tag and release for the project inside GitHub.

## Inputs

### `config-json`

**Required** JSON string containing workflow config parameters.

### `github-token`

**Required** GitHub token for authentication.

## Example Usage

```yaml
name: CI

on: [push]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2

    - name: Run GAWG Release Action
      uses: alvarogarciapiz/gawg-release@main
      with:
        config-json: '{"PROJECT_NAME":"gawg","PROJECT_VERSION":"0.0.1","RELEASE":"enabled","RETENTION_DAYS":"1","JAVA_VERSION":"8","PYTHON_VERSION":"3.10","NODE_VERSION":"18","NODE_DIST_DIR":"dist/","PYTHON_DIST_DIR":"./","JAVA_DIST_DIR":"target/","JAVA_DISTRIBUTION":"temurin","TESTING":"enabled"}'
        github-token: ${{ secrets.GITHUB_TOKEN }}
````
## What It Does
1. Checks if the release is enabled.
2. Sets up Git configuration.
3. Generates a workflow summary report.
4. Generates a tag based on the project version.
5. Creates a release with the content of summary.txt as the release notes.