---
name: New Day
description: Add the current UTC daily update to the sample page when it is missing.
engine: copilot
on:
  schedule: daily
  workflow_dispatch: {}
permissions:
  contents: read
  copilot-requests: write
tools:
  edit: true
safe-outputs:
  create-pull-request:
    title-prefix: "[new-day] "
    max: 1
    allowed-files:
      - index.html
    if-no-changes: ignore
    fallback-as-issue: false
---

# New Day

Use the workflow run's UTC date.

Update only [index.html](index.html) and preserve every existing daily update.

Follow the existing daily-updates structure, ID conventions, date wording, and styling.

## Process

1. Find the existing Daily Updates navigation entry and its matching dialog markup.
2. Check whether the workflow run's UTC date is already present.
3. If the UTC date is already present, make no change and call `noop`.
4. If the UTC date is missing, add exactly one new navigation control and exactly one matching accessible dialog.
5. Keep the new entry consistent with the existing pattern:
   - use the same style of visible date wording
   - use matching lowercase hyphenated IDs
   - keep the dialog labeled and described for accessibility
   - place the new dialog alongside the existing daily update dialogs
6. Do not duplicate an existing date, navigation control, or dialog.
7. Use the `edit` tool for all file changes.

## Content Requirements

- The new dialog must confirm that the daily update ran.
- The change must stay limited to `index.html`.
- Do not modify `styles.css`.
- Keep the update brief and consistent with the current page copy.