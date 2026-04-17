# Copilot Instructions — norsk-studieark

## Project overview

This repository contains printable Norwegian language study sheets (studieark) designed for A4 paper. Each study sheet is an HTML file with a matching PDF. The vocabulary data lives in CSV files.

## File structure

- `norsk-studieark.html` / `.pdf` — Base-level reference (conjunctions, prepositions, pronouns, etc.)
- `norsk-studieark-b1.html` / `.pdf` — B1-level vocabulary reference (nouns by topic)
- `norsk-studieark-verbs.html` / `.pdf` — Verb reference (essentials, modals, phrasal, 400+ common verbs)
- `vocab-nouns.csv` — Noun vocabulary data organised in paired columns (Norwegian, English) per topic category
- `vocab-verbs.csv` — Verb vocabulary data with similar paired-column structure

## Key conventions

### HTML study sheets

- All study sheets are single self-contained HTML files (inline CSS, no external dependencies).
- Use compact typography optimised for print: `7pt` body, `6pt`–`6.5pt` word entries, tight padding.
- Each section has a colour-coded header (`h2` with white text on coloured background) and optional subheaders (`h3`).
- Word entries use the pattern: `<span class="no">Norwegian</span> — <span class="en">English</span>`.
- Use `break-inside: avoid` on entries and `break-after: avoid` on headers to keep content together across columns.
- Include `-webkit-print-color-adjust: exact; print-color-adjust: exact;` on coloured elements so backgrounds print.
- Use `@media print` with `@page { margin: 4mm; size: A4; }`.

### PDF generation

**A PDF must always be generated after any HTML change.** Use:

```bash
chromium --headless --disable-gpu --no-sandbox \
  --print-to-pdf="<name>.pdf" \
  --print-to-pdf-no-header \
  "$(pwd)/<name>.html"
```

### CSV data format

- Row 1 contains category headers in every other column (col 0, 2, 4, …).
- Each category occupies two columns: Norwegian term, English translation.
- Data rows start at row 2.

### Commit messages

- Use descriptive commit messages summarising what changed.
- Always include the trailer: `Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>`
