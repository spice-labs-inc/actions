### Spice Grinder Action
Used to scan your systems and upload the results to a Spice Labs server.

### Example Usage in Workflow
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

      - name: Run Spice Grinder Scan & Upload
        uses: spice-labs-inc/actions/spice_grinder_scan@main  # Or use a tagged release like @v1
        with:
          repository_url: https://github.com/example/project.git  # Leave blank if using local path
          branch: main
          file_path: ""  # Optional: path to local files to scan instead of repo clone
          config: /input/spicegrinder.yml
          mode: public
        env:
          GRINDER_JWT: ${{ secrets.GRINDER_JWT }}
```
