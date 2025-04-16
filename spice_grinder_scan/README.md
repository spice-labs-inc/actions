### Action for Spice Grinder Scan

A reusable GitHub Action to scan source code with [Spice Grinder](https://github.com/spice-labs-inc/grinder), and optionally upload the results.

This action supports:
- Cloning a target repository or scanning local files
- Running Grinder inside a secure container
- Uploading results using a JWT

---

### Inputs

| Name              | Description                                                     | Required | Default |
|-------------------|------------------------------------------------------------------|----------|---------|
| `repository_url`  | URL of the repository to clone and scan                         | false    | `""`    |
| `branch`          | Branch to check out when cloning from `repository_url`          | false    | `main`  |
| `file_path`       | Path to local files to scan (alternative to `repository_url`)   | false    | `""`    |
| `config`          | Path to the Spice Grinder config file (inside container)        | true     | —       |
| `mode`            | Upload mode (`public`, `private`, etc.)                         | true     | —       |

---

### Environment Variables

| Name            | Description                  | Required |
|------------------|------------------------------|----------|
| `GRINDER_JWT`    | JWT token for uploading results | true     |

---

### Example Usage

```yaml
name: Scan with Spice Grinder

on:
  workflow_dispatch:

jobs:
  scan-and-upload:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Run Spice Grinder Scan
        uses: spice-labs-inc/actions/spice_grinder_scan@main
        with:
          repository_url: https://github.com/example/project.git
          branch: main
          config: /input/spicegrinder.yml
          mode: public
        env:
          GRINDER_JWT: ${{ secrets.GRINDER_JWT }}
```
