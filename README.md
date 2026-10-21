# Backstay Examples

Sample documents for **Backstay**, a native macOS app for structured
text: an outline on the left, a page, form or table view in the middle,
and a blueprint (JSON Schema) behind every field. A document is a
`.backstay` bundle — a folder of JSON files holding the data and its
schema side by side, readable by any text editor and by Backstay.

## Status

Backstay is in private testing (TestFlight, internal testers by
invitation). These bundles match **Backstay 0.7.0, build 2282
(2026-10-21)** and later. Backstay reads exactly one file format — there
are no soft migrations — so whenever the format changes, this repository
gets a new snapshot and this line changes with it.

## Opening an example

Clone or download this repository, then open a `.backstay` folder in
Backstay (File › Open…, or drag the folder onto the app icon). Each bundle
is self-contained: it imports Backstay's built-in schemas
(`backstay:document`, `backstay:literature`, …), which ship with the app.

## The examples

| Bundle | What it shows |
| --- | --- |
| `mein-erstes-projekt.backstay` | The smallest document: one file holds the data and its types (`$types`). Start here. |
| `firma.backstay` | Plain JSON data with a schema — a company with departments, employees, products and customers. Tables, nested records, the join of two marked tables. |
| `anker-demo.backstay` | Anchors on words: a value computed by a formula directly at the word, a query, an address, a link; the anchor tab. |
| `zellen-demo.backstay` | Cells that compute from other cells: literals, defaults at the type, defaults at the field, and prose that references them. |
| `projekt.backstay` | A root with an outsourced document and notes (file markers), one window per module. |
| `beispiel-hausarbeit.backstay` | A complete term paper in the Cologne NDL style: chapters and paragraphs, footnotes with the full citation cascade, a bibliography (hand entries plus a Zotero buffer), formulas in prose and a procedure that counts words, matrices as tables, a title page with logo, Markdown and Word export. |

The bundles are in German — Backstay's first users write German term
papers. Field keys are English.

**About `beispiel-hausarbeit`:** it is a fictional sample paper written
for this project and makes no scholarly claim. The author "Lena
Musterfrau" is invented. The declaration of academic honesty is the
standard text of the University of Cologne.

## How this repository is produced

The examples are maintained in Backstay's main repository. Each bundle
here is written with Backstay's command-line tool:

```
backstay write SOURCE.backstay --to TARGET.backstay          # canonical form, companion files copied
backstay write SOURCE.backstay --to TARGET.backstay --check  # verify: exit 0 = identical
```

## License

The examples in this repository are licensed under the
[Creative Commons Attribution 4.0 International License](LICENSE)
(CC BY 4.0). Backstay itself — the app and its source — is a separate
work under the Business Source License 1.1 and is not part of this
repository.
