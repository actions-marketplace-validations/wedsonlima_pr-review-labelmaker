# PR Review Labelmaker
Automatically label pull requests based on events

## Create Workflow
Create a workflow (eg: .github/workflows/pr_review.yml see Creating a Workflow file) to utilize the labeler action with content:

```yml
on:
  pull_request_review:
    types: [submitted]

jobs:
  labeler:
    runs-on: ubuntu-latest
    steps:
    - uses: wedsonlima/pr-review-labelmaker@v0.0.5
      with:
          repo-token: ${{ secrets.GITHUB_TOKEN }}
          target-approved-count: 1
          label-to-be-added: 'Accepted'
          label-to-be-removed: 'In Review'
```

## Inputs
Various inputs are defined in [`action.yml`](action.yml)

| Name | Description | Default | Required |
| - | - | - | - |
| `repo-token` | Token to use to authorize label changes. Typically the GITHUB_TOKEN secret | N/A | N/A |
| `target-approved-count` | The target approved review count | 0 | Y |
| `label-to-be-added` | The GitHub label to be added when `target-approved-count` is reached | None | Y |
| `label-to-be-removed` | The GitHub label to be removed when `target-approved-count` is reached | None | N |

## How to build

```bash
$ npm run build && npm run package
```
