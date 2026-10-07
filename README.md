# U1 Sheets

**A spreadsheet application. Open, edit and save the files you already have.**

Part of the [UnsoftOne](https://github.com/temidayoxyz/unsoftone) suite.

```
Download. Install. Work.
```

No account. No subscription. No sign-in. No internet connection. No telemetry.
Your files stay on your disk, in standard formats, readable by any other
software.

---

## Status: not started

**Nothing has been built yet.** This repository is a placeholder holding the
project's direction and history so that work can start cleanly and be picked up
without reconstructing context.

U1 Sheets begins after U1 Docs is genuinely working. That sequencing is
deliberate — see
[ADR-0008](https://github.com/temidayoxyz/unsoftone/blob/main/docs/adr/0008-product-sequencing-u1-docs-first.md).
Designing four products in parallel produces four shallow applications.

---

## What this will be

U1 Sheets is intended to be a **serious** spreadsheet application — capable of
opening, editing, saving and exporting the files people already encounter in the
Microsoft Office ecosystem.

### Two problems dominate, and both are worth understanding up front

These are the hard parts of spreadsheets specifically, and neither is "drawing
a grid":

**1. Formula recalculation.** Excel's function set is enormous, and real files
routinely store a *cached* result rather than a recalculated one. Deciding what
an application does with a stale cache — trust it, recompute it, or warn — is a
correctness problem before it is an engineering problem. Getting it wrong means
silently wrong numbers, which is the worst possible failure mode for a
spreadsheet.

**2. Number formats and dates.** Serial date systems, custom number format
codes, and locale interaction. It is a deep, low-glamour rabbit hole that users
notice immediately when it is wrong — a date that renders as a number, or a
currency that drops its symbol.

### Feature depth, in priority order

1. Cell grid, selection, keyboard navigation
2. Data types: text, number, boolean, date, error
3. Number formatting and date formatting
4. Formulas and the core function set
5. Recalculation and the dependency graph
6. Named ranges, absolute and relative references
7. Formatting: fonts, fills, borders, alignment
8. Multiple sheets, navigation, structure
9. Sort, filter, freeze panes
10. Charts
11. Import and export: CSV, XLSX, PDF

---

## Compatibility

Tracked in the
[ecosystem compatibility matrix](https://github.com/temidayoxyz/unsoftone/blob/main/docs/compatibility.md).

| Format  | Status                                |
| ------- | ------------------------------------- |
| `.csv`  | Planned. Encoding detection is the fiddly part. |
| `.tsv`  | Planned.                              |
| `.xlsx` | Primary target. Not started.          |
| `.ods`  | After XLSX.                           |
| `.xls`  | Legacy binary. Deliberately not committed to. |

---

## Prior research

Not commitments — the ecosystem is more helpful here than for DOCX, and it is
worth knowing before starting:

| Crate                                              | Role                        |
| -------------------------------------------------- | --------------------------- |
| [`calamine`](https://crates.io/crates/calamine)     | reads XLSX and ODS          |
| [`rust_xlsxwriter`](https://crates.io/crates/rust_xlsxwriter) | writes XLSX         |
| [`umya-spreadsheet`](https://crates.io/crates/umya-spreadsheet) | reads and writes XLSX |

**None of these is a lossless round-trip editor.** The lossless requirement in
[ADR-0005](https://github.com/temidayoxyz/unsoftone/blob/main/docs/adr/0005-ooxml-lossless-layer.md)
applies here too: features we cannot edit must be preserved untouched, not
dropped.

---

## Building

Nothing to build yet. This project is Rust — see
[ADR-0001](https://github.com/temidayoxyz/unsoftone/blob/main/docs/adr/0001-rust-first-architecture.md).

---

## Contributing

Read [CONTRIBUTING.md](CONTRIBUTING.md) first.

**This project is not ready for feature contributions.** The most useful
contributions right now are discussion and real-world `.xlsx` files that break
things — particularly ones with unusual formulas, number formats, or
cross-sheet references. Redact anything you are not permitted to share.

Please do not send documents containing anything you do not have permission to
share.

---

## Related

| Project                      | What it is                            |
| ---------------------------- | ------------------------------------- |
| [`unsoftone`](https://github.com/temidayoxyz/unsoftone) | Ecosystem direction, ADRs, roadmap |
| [`u1-docs`](https://github.com/temidayoxyz/u1-docs)     | Word processing — in progress        |
| [`u1-slides`](https://github.com/temidayoxyz/u1-slides) | Presentations                       |
| [`u1-notes`](https://github.com/temidayoxyz/u1-notes)   | Notes                                |

## License

[GPL-3.0](LICENSE) ·
[ADR-0006](https://github.com/temidayoxyz/unsoftone/blob/main/docs/adr/0006-license-gpl-3.md)
