### cargo-version-check
Checks GitHib Release tag matches Cargo.toml version number and fails if they mismatch

#### Check Cargo Version Matches Tag
This GitHub Action ensures that the Git tag (e.g. `v1.2.3`) matches the version in `Cargo.toml`.

#### Usage
```yaml
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Check Cargo version matches tag
        uses: spice-labs-inc/cargo-version-check@v0.0.2
```
#### Complete Workdflow Task
```yaml
jobs:
  check-version:
    name: Ensure Git tag matches Cargo.toml version
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Check Cargo version matches tag
        uses: spice-labs-inc/cargo-version-check@v0.0.2
```
