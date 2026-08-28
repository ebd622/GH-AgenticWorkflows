---
name: Highlights of the Day
description: Add an unused GitHub Agentic Workflows FAQ highlight to the site.
on:
  schedule: every 6 hours
  workflow_dispatch:
permissions:
  contents: read
  copilot-requests: write
tools:
  edit: true
  web-fetch: {}
network:
  allowed:
    - github.github.com
safe-outputs:
  create-pull-request:
    allowed-files:
      - index.html
    max: 1
engine: copilot
---

# Highlights of the Day

## Task

Use the workflow run's current UTC date and fetch the GitHub Agentic Workflows
FAQ from https://github.github.com/gh-aw/reference/faq/. Read `index.html` and
select one FAQ question that is not already represented there. Do not invent an
FAQ or alter its meaning; write a concise, accurate answer based on the FAQ.

Before editing, check all existing Daily Updates navigation controls, dialogs,
questions, and answers. Never duplicate a date, navigation control, dialog, or
FAQ. If today's dialog already contains an FAQ, or if no unused FAQ remains,
make no change and use `noop` with a brief explanation.

When an unused FAQ is available, use the UTC date to locate today's matching
Daily Updates entry. If today's entry has a placeholder dialog, reuse it.
Otherwise, edit `index.html` to add one navigation control and one matching
dialog. Add the selected FAQ question and concise answer to that dialog.

Follow the existing HTML structure, ID conventions, date wording, and styling.
Use the existing native dialog pattern: a button with
`aria-haspopup="dialog"`, `aria-controls`, and `data-dialog-trigger`, plus a
dialog with matching `aria-labelledby` and `aria-describedby` IDs. Use ordinal
date wording like `1st of August`, preserve every existing daily update, and
ensure the question and answer are accessible through the dialog labels.

Edit only `index.html`; do not modify `styles.css` or any other file. Use the
configured safe output to propose at most one pull request. Validate this
workflow with `gh aw validate highlights-of-day`, but do not compile it.

## Safe Outputs

- Use the configured `create-pull-request` safe output only for changes to
  `index.html`, with a maximum of one pull request.
- Use `noop` when today's FAQ is already present or no unused FAQ remains.