Reusable GitHub Workflows
=========================

Actionlint
----------

Runs `actionlint` on GitHub workflows.

```yml
---

on:
  pull_request:
    paths:
      - .github/workflows/*.yml
  push:
    paths:
      - .github/workflows/*.yml

jobs:
  call-workflow:
    uses: wookietreiber/workflows/.github/workflows/github-actionlint.yml@main

...
```

Rust
----

- runs `cargo fmt --check` and `cargo clippy` on stable or whatever
  `rust-toolchain.toml` says
- detects MSRV using `cargo-msrv`
- runs `cargo check`, `cargo build` and `cargo test` on both detected MSRV and
  stable or whatever `rust-toolchain.toml` says

```yml
---

jobs:
  call-workflow:
    uses: wookietreiber/workflows/.github/workflows/rust.yml@main

...
```

Runs `cargo audit` via `rustsec/audit-check`:

```yml
---

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
