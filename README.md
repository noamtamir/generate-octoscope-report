# Octoscope Report Generator

This GitHub Action generates a comprehensive report about your GitHub Actions usage to help you understand and optimize your CI/CD workflows.

## Example

```yaml
name: Generate Octoscope Report

on:
  schedule:
    - cron: '0 0 * * 0'  # Weekly on Sunday midnight UTC
  workflow_dispatch:

jobs:
  generate-report:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Generate octoscope report
        uses: noamtamir/generate-octoscope-report@v1.0.2
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
```

## What It Does

1. Authenticates using the workflow's `GITHUB_TOKEN`
2. Installs the Octoscope GH CLI extension
3. Generates a detailed GitHub Actions usage report covering the last 7 days
4. Uploads the report to Octoscope servers where it will be available for 72 hours
5. Provides a unique URL to access your report in the action output

## Requirements

- GitHub-hosted runners

## More information
You can get more information about octoscope gh extension in the [extension repo](https://github.com/noamtamir/gh-octoscope).
If you wish to permenantly delete your data you can do so with the extension: `gh octoscope report delete <report_id>`. More information can be found in the link above.