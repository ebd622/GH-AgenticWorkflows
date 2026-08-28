---
name: Weekly Report Status
description: Generate a weekly repository activity report.
on:
  schedule:
    - cron: "0 9 * * 1"
  workflow_dispatch:
permissions:
  contents: read
  issues: read
  pull-requests: read
  copilot-requests: write
engine: copilot
tools:
  github:
    mode: gh-proxy
    toolsets: [default]
safe-outputs:
  create-issue:
    title-prefix: "[weekly-report] "
    max: 1
---

# Weekly Report Status

## Task

Generate a concise activity report for the previous seven full days ending at
workflow start time in UTC. Review repository commits, issues, and pull
requests created or updated during that window. Summarize the key activity and
include counts and links where useful.

Publish the report as a new issue using the configured `create-issue`
safe-output. The issue title must start with `[weekly-report] `. Clearly state
when no commits, issues, or pull requests occurred during the reporting window.
Create no more than one issue for this run.

Format the issue with `###` section headings, a short overview, visible summary
counts, concise details, and the UTC reporting window. Do not invent activity
or classifications. Create the issue even when the reporting window contains
no activity, and state clearly which of commits, issues, and pull requests had
no activity.

## Safe Outputs

- Use the configured `create-issue` safe output for the single report issue.