# Refactoringminer-ASTDiff-Exporter


**Refactoringminer-ASTDiff-Exporter** is a GitHub Action that runs RefactoringMiner to generate AST Diff and provides screenshot from the diff. This tool can be used for analyzing code changes and refactoring between versions in a GitHub repository.

## Features

- Executes RefactoringMiner to generate an AST Diff for any commit or pull request.
- Generates the webdiff artifact.
- Generates AST Diff screenshots.
- Easy to integrate into your GitHub workflows.

## Usage

### Inputs

| Name       | Description                           | Required |
|------------|---------------------------------------|----------|
| `OAuthToken` | Github OAuthToken for authentication        | Yes (Only for private repos)|
| `URL`       | URL of the commit for the diff | Yes      |
| `Screenshot`       | Name of the file to take the screenshot of  | No      |

### Outputs

| Name         | Description                                     |
|--------------|-------------------------------------------------|
| `artifact_path` | Path to the generated diff artifact (Exported webdiff) |
| `screenshots_path` | Path to the taken screenshots   |


Please visit https://api.imgbb.com/ to get your API key. You are supposed to have this secret in your repo/org as `secrets.IMGBB_API_KEY.`

Note: You can generate an OAuth token in GitHub Settings -> Developer settings -> Personal access tokens.

### Example Workflow

```yaml
name: Generate AST Diff

on:
  push:
    branches:
      - main

jobs:
  generate-diff:
    runs-on: ubuntu-latest

    steps:
      - name: Run ASTDiff Bot
        uses: pouryafard75/refactoringminer-astdiff-exporter@v1.1
        with:
          OAuthToken: ${{ secrets.GITHUB_TOKEN }}
          URL: https://github.com/Alluxio/alluxio/commit/9aeefcd8120bb3b89cdb437d8c32d2ed84b8a825
          Screenshot: MaxFreeAllocator

```

## Interesting Use Cases
Checkout our wiki to find more interesing [examples](https://github.com/EmpiricalSEConcordia/Refactoringminer-Astdiff-Exporter/wiki/Examples)



