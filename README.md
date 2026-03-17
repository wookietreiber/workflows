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

Rust
----

Runs `cargo audit` via `rustsec/audit-check`:

```yml
---

name: rust-audit

on:
  pull_request:
  push:
  schedule:
    - cron: '0 6 * * 1'

jobs:
  call-workflow:
    uses: wookietreiber/workflows/.github/workflows/rust-cargo-audit.yml@main
    secrets:
      token: ${{ secrets.GITHUB_TOKEN }}

...
```
