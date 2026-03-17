Reusable GitHub Workflows
=========================

Actionlint
----------

Runs `actionlint` on GitHub workflows.

```yml
---

name: actionlint

on:
  pull_request:
    paths:
      - .github/workflows/*.yml
  push:
    paths:
      - .github/workflows/*.yml

jobs:
  call-workflow:
    name: actionlint
    uses: wookietreiber/workflows/.github/workflows/github-actionlint.yml@main

...
```
