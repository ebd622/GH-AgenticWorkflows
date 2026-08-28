---
name: New Day
description: Add the daily UTC update to the site's Daily Updates section.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
  copilot-requests: write
tools:
  edit: true
safe-outputs:
  create-pull-request:
    allowed-files:
      - index.html
    max: 1
engine: copilot
---

# New Day

## Task

Use the workflow run's current UTC date. Inspect `index.html` before making any
change. If that UTC date is already present in the existing Daily Updates
navigation or matching dialog, make no change and use `noop` with a brief
explanation.

Otherwise, edit only `index.html` to:

1. Add one navigation control for the date to the existing `Daily Updates`
   navigation.
2. Add one matching accessible `<dialog>` confirming that the daily update ran.

Follow the existing HTML structure, ID conventions, date wording, and styling.
Use the existing native dialog pattern: a button with `aria-haspopup="dialog"`,
`aria-controls`, and `data-dialog-trigger`, plus a dialog with matching
`aria-labelledby` and `aria-describedby` IDs. Use the same ordinal date wording
as the existing entries, such as `1st of August`, and make the dialog content
clearly confirm that the daily update ran on that date.

Preserve every existing daily update. Do not duplicate a date, navigation
control, or dialog. Do not modify `styles.css` or any file other than
`index.html`. Validate this workflow with `gh aw validate new-day`, but do not
compile it.

## Safe Outputs

- Use the configured `create-pull-request` safe output for the change, limited
  to `index.html` and at most one pull request.
- Use `noop` when the UTC date is already present and no change is needed.