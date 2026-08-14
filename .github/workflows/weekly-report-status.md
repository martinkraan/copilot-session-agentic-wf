---
name: Weekly Report Status
description: Create a weekly repository activity report issue for the previous seven days.
engine: copilot
on:
  schedule:
    - cron: "0 0 * * 1"
  workflow_dispatch: {}
permissions:
  contents: read
  issues: read
  pull-requests: read
  copilot-requests: write
safe-outputs:
  create-issue:
    title-prefix: "[weekly-report] "
    max: 1
---

# Weekly Report Status

Create a concise activity report covering the previous seven days.

Include these sections:

- Commits
- Issues
- Pull requests

Requirements:

- Summarize the most important activity rather than listing everything.
- Clearly state when a category had no activity.
- If there was no activity at all, say that explicitly.
- Publish the report as a new issue.
- Keep the report brief, factual, and easy to scan.