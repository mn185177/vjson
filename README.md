# validate-json

This action validates json files. The action scans the repository for files with the .json extension, and tries to unmarshall them. If there are unmarshalling errors, the action terminates and your workflow will break. It will log all errors encountered before exiting.

The action is run using a Docker container and is written in Go.

## Inputs
- `directory`: (string, optional) The path on which to scan .json files, defaults to `.`, in which case it scans the whole repository.

## Usage
Complete sample workflow. For mor information see the [action.yml](action.yml), and the GitHub help documentation here https://docs.github.com/en/actions/using-workflows#creating-a-workflow-file
```yaml
name: Validate json files

on:
  pull_request:
    branches: [ master ]

jobs:
  validate-json:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v3
      with:
        fetch-depth: 2

    - name: Validate json files
      uses: mn185177/validate-json@master
      with:
        directory: "." #

```
