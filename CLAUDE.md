# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

This is **not a software project** — it's a Quarto book (`buggy_bar.Rproj` / `_quarto.yml`, `project: type: book`) documenting how to build a "Buggy Bar," a kite control bar designed by Philip Chase. The entire book is a single chapter, `index.qmd`, rendered to HTML in `_book/`. Prior versions used Bookdown; the project migrated to Quarto (see CHANGELOG.md "Migrate from Bookdown to Quarto Book").

## Common commands

- Render the book: `quarto render` (outputs to `_book/`)
- Preview with live reload: `quarto preview`
- There are no tests, linters, or build scripts beyond Quarto rendering — this is documentation/content authoring.

## Structure

- `index.qmd` — the entire book content (single chapter). Sections follow the physical build process in order: Overview → Bill of materials → Tools required → Component construction (Control bar, Trim Line, Cleat Jacket, Separation block, Flag line, Stub line, Bar End Loops, Steering Lines) → Assembly.
- `images/` — all photos and diagrams referenced from `index.qmd` via Quarto figure syntax (`![caption](images/foo.jpg){#fig-id ...}`), cross-referenced in prose with `@fig-id`.
- `_quarto.yml` — book project config (title, chapter list, HTML theme `yeti`).
- `references.bib` / `packages.bib` — bibliography files (largely vestigial from the Bookdown era; `references.bib` is empty).
- `style.css` — minor HTML styling tweaks for captions and code blocks.
- `_book/` — rendered output (checked in; regenerate with `quarto render` after content changes).
- `CHANGELOG.md` — version history of the *build design* (bar revisions, component changes), not of this repo's code. Update it when documenting a design change to the bar (new BOM items, replaced components, etc.), following Keep a Changelog / SemVer style already in use.

## Editing conventions

- New images go in `images/` and are referenced with relative paths `images/<file>.jpg`; give each figure an `#fig-<kebab-case-id>` label and `fig-alt` text, and cross-reference it in the prose with `@fig-<id>`.
- Footnotes use Quarto's `[^index-N]` syntax with the definition at the bottom of the relevant section.
- Section headers map directly to build steps performed in physical order — when adding a new build step or component, place it in the matching position in that sequence, and update the Bill of Materials / Tools list if it introduces new parts or tools.
- After editing `index.qmd`, run `quarto render` to confirm the book builds and to refresh `_book/` before committing.
