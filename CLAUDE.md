# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Repo Is

**ted-model2owl-docs** is the **Antora/AsciiDoc documentation** for the **model2owl** tool
(the XSLT transformation engine that converts UML conceptual models into OWL/SHACL/etc.).
This repo contains only prose and diagrams — no transformation logic. It is the **published
source of truth** for the docs, served at <https://docs.ted.europa.eu/M2O/latest/>.

The tool itself lives in the **model2owl** repo (this repo's sibling). Treat model2owl as
authoritative for *actual behaviour*; when the docs and the code disagree, the code wins and
the docs must be corrected.

## Structure

- `antora.yml` — Antora component descriptor (component `M2O`, `version: '3.1.0'`).
- `modules/ROOT/pages/**/*.adoc` — all documentation pages.
- `modules/ROOT/nav.adoc` — the left-hand navigation. **Update it whenever you add, move,
  rename, or remove a page** (a page not listed here is unreachable from the menu).

Page groups:
- `checkers/model2owl-checkers.adoc` — the convention-checker reference **table** (see Editorial sync).
- `transformation/transf-rules{1..4}.adoc` — transformation rules (`C.*` classes/attributes,
  `R.*` connectors, `D.*` datatypes/enums, `T.*` descriptors).
- `uml/*.adoc` — UML modelling conventions, incl. `unsupported-uml-constructs.adoc` and `conceptual-model-conventions.adoc`.
- `user-guide/*.adoc` — `how-to-use.adoc` (make targets/parameters), `configuration-file.adoc`
  (config-parameters.xsl variables + metadata.json fields), `respec-documentation.adoc`, `rdf-diffing.adoc`.

## Building / previewing

In practice, **validate edits by review**: check AsciiDoc syntax by eye and keep
cross-references/anchors consistent (below). To produce the rendered site from the sources
on GitHub, run the manual workflow
<https://github.com/meaningfy-ws/model2owl-docs-gh-pages/actions/workflows/docs.yml>.

## Editorial content is mirrored from the model2owl code — keep it in sync

This is the most important rule. Several user-facing strings are **duplicated** between the
model2owl **code** (XSLT) and the pages here; the docs must match what the code actually emits.

- **Convention-checker messages, severities, and rule IDs.** Each checker in model2owl's
  `src/html-conventions-lib/**` emits a message (via `f:generate{Error,Warning,Info}Message`)
  tagged with a **rule ID**. Those are mirrored, **keyed by rule ID**, in the big table in
  `checkers/model2owl-checkers.adoc` (columns: `rule id | severity | checker name | message |
  pseudo-code`). A row's **message** must equal the emitted string (ignoring `$placeholder$`
  tokens that stand in for dynamic values), and its **severity** must match the function family
  (`Error`→error, `Warning`→warning, `Info`→info — exactly those three words).
- **"Unsupported UML constructs"** warnings ↔ `uml/unsupported-uml-constructs.adoc`.
- **Transformation-rule descriptions** ↔ `transformation/transf-rules*.adoc`.

When a code change alters any such string/severity/rule-ID, the matching docs entry must be
updated **in the same change**. The model2owl repo owns the authoritative mapping and a skill
(`syncing-editorial-text-with-docs`) that lists every linked place and the impact-analysis
procedure — use it from there when a code change is involved.

Checker-table conventions:
- Rows whose ID ends in `--0` or whose pseudo-code says *"inherits"* are **table-inheritance
  markers**, not real checker emissions — do not treat them as code that's missing a rule.
- The page has in-file editing instructions near the top; follow them.

## Make targets & config parameters are documented here — keep in sync with the Makefile

`user-guide/how-to-use.adoc` lists model2owl's `make` targets and their `KEY=VALUE`
parameters, and `user-guide/configuration-file.adoc` documents the `config-parameters.xsl`
variables and `metadata.json` fields. When model2owl renames/removes/repurposes a target,
an overridable variable, or a config parameter, update these pages to match.

## AsciiDoc house style & conventions

- **Admonitions:** use the **block** form, not the inline `NOTE:` form:
  ```
  [NOTE]
  ====
  Body text.
  ====
  ```
- **The product name is `model2owl`** (lowercase). Keep it lowercase mid-sentence; only
  capitalise it at the **start of a sentence** → `Model2owl`. Don't bold/emphasise the name
  gratuitously.
- **Cross-references:** `xref:path/file.adoc#anchor[link text]`. Anchors are defined as
  `[[anchor]]` or `[#anchor,…]`. When you rename a page or an anchor, fix every inbound `xref:`
  **and** `nav.adoc`.
- **Embedded links from the code are stable contracts.** model2owl's generated artefacts embed
  URLs into this site (e.g. the convention report links to
  `…/uml/conceptual-model-conventions.html` and `…/uml/unsupported-uml-constructs.html#…`).
  Renaming those pages/anchors breaks those links — coordinate such renames with the code.
- **Transformation-rule codes** use AsciiDoc counters: `{counter:rule-cnt:C.01}` seeds the
  numbering and `rule:<slug>` anchors are used for xrefs. Keep zero-padding consistent (`D.01`,
  not `D.1`).

## Git & contribution workflow

- This is a **fork**: `origin` = `meaningfy-ws/ted-model2owl-docs` (work here), `upstream` =
  `OP-TED/ted-model2owl-docs`. Commit and push to **`origin`**; open PRs against **`develop`**.
- **Commit messages:** plain imperative subjects — **no** Conventional-Commits prefixes
  (no `fix:`/`feat:`/`docs:`).
- Changes that mirror a code change should reference it so the two stay traceable.

## Provenance — git-ignored paths are local-only

Treat any git-ignored path as **sealed**: its existence and contents must never surface in
commits, PR titles/descriptions, page content, or changelog entries. If unsure whether a path
is ignored, run `git check-ignore <path>`.
