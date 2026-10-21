# design-system — Agent Guide

## What this is

The studio-wide visual and verbal language. Documentation and assets only — no
build, no dependencies, no site.

| File | What it is |
| :--- | :--- |
| [`tokens.md`](./tokens.md) | Token values: shared layer, then the product values, then known drift |
| [`guidelines.md`](./guidelines.md) | The language: core (1–7), the rules for every surface (8–27: voice, accessibility, icons, motion, interface patterns, charts, code, marketing and docs sites, desktop apps, Obsidian plugins, CLI and install scripts, repositories, release notes, app icons and installers, screenshots, social images, email, the new-product checklist), decisions (28), adoption (29) |
| [`brand/`](./brand/README.md) | Official marks, badges and raster exports |
| [`canvas.html`](./canvas.html) | The same system as a browsable 10-page document |

`canvas.html` is the reviewable artefact. When a rule is unclear, open it in a
browser and look at the rendered pages rather than re-reading the prose.

## The rule that resolves every conflict

**The shipped codebase is authoritative. These documents are the bug.**

`tokens.md` states it directly. Theorem's
`src/core/styles/design-tokens.css` and `src/core/lib/design-tokens.ts` are the
reference implementation of the whole token layer.

Nothing here is imported programmatically by any product. Adoption is by hand,
which is exactly why that rule matters: when you find a disagreement, you have
found a documentation bug, not a code bug — unless the disagreement is one the
system is meant to prevent, in which case fix both and say so.

## The non-negotiables

From `tokens.md`. These are not defaults to be negotiated per product:

- **One dark base**: `#141416`. Never negotiated. Carbon `#12140f` is the mark
  field, not the base.
- **Corner radius `0`** on every element, without exception. Not a card, not a
  button, not an avatar, not a spinner.
- **One accent for the whole lab, one meaning**: acid lime `#c6f135`. No
  product keeps its own.
- **DM Sans / DM Mono at 300 and 400 only.** Hierarchy from size and colour,
  never from extra weights.
- **Type is set at two weights, tracking is a token** (`--tracking-display`
  `-0.03em`, `--tracking-headline` `-0.02em`, `--tracking-body` `-0.01em`).
- **Marks are used unchanged.** Never redraw one, never type it as characters,
  never round, rotate, skew or outline it. The official SVG governs; values
  quoted in prose are reference only.
- **The credit line** is `Made by Fundaments.work`, DM Mono, 0.35 × wordmark.

## Products

| Product | Accent | Note |
| :--- | :--- | :--- |
| Theorem | acid lime `#c6f135` | Reference implementation |
| Manang | acid lime `#c6f135`, sage `#b3d17a` for math | First desktop-shell consumer; its `DESIGN.md` is the source for the density and syntax rules |
| fundaments-landing | acid lime `#c6f135` | Studio site |
| theorem-landing | acid lime `#c6f135` | Adopts the shared base |
| Lemma | **out of scope** | Runs inside Obsidian and must inherit its theme |

**Lemma is outside the system by decision, not omission.** Do not "fix" it by
pulling lab tokens into the plugin UI. Its published surfaces (README, badge,
release notes) still follow the lab's rules, and
[section 19 of the guidelines](./guidelines.md#19--obsidian-plugins) says exactly
what applies and what does not.

## Where a rule lives

Ask which surface you are on, then read its section; do not infer from another.

| You are making | Read |
| :--- | :--- |
| A marketing site or landing page | guidelines 16 |
| A docs site (Starlight) | guidelines 17 |
| A desktop app (Tauri, Svelte) | guidelines 18, tokens: Desktop density |
| An Obsidian plugin | guidelines 19 |
| A CLI, terminal output or an install script | guidelines 20, tokens: Terminal output |
| A README, repository settings, issue forms | guidelines 21 |
| Release notes or a changelog | guidelines 22 |
| An app icon or an installer | guidelines 23, tokens: App icons |
| A screenshot or a demo | guidelines 24 |
| A chart or a diagram | guidelines 14, tokens: Chart colours |
| A table, form, error or empty state | guidelines 13 and 9 |
| Anything with words | guidelines 9 |
| A new product | guidelines 27, the checklist |

The rules that apply to everything: accessibility (10), icons (11), motion (12),
code (15).

## Editing this repo

- `tokens.md` ends with two tables that are the point of the file, not an
  appendix: **Known drift** and **Adoption status**. Keep them.
- **Known drift is a ledger, not a wishlist.** Add a row when you find a
  disagreement. Do not quietly fix one and delete the row — mark it Fixed and
  say how, as the existing rows do. A drift entry that disappears without a
  resolution is indistinguishable from one that was never found.
- **Adoption status is per product, per layer**: base, radius, type, spacing,
  motion. "Specified is not the same as adopted." Spacing is currently the one
  gap across the products that adopted the system.
- Bump the version and date line at the top of `tokens.md` when you change
  values, not when you fix prose.
- **A rule needs a value that does not exist? Add it to `tokens.md` first**, in
  Extended tokens or Component dimensions, marked **new**, and add a row to
  Adoption status saying nobody has adopted it. Never put an unrecorded number
  in `guidelines.md`.
- **Compute contrast, do not estimate it.** A ratio in these files is measured
  on the real values. If you change a token, recompute every pair it appears in
  (the pairing table in `tokens.md`) and the guidelines contrast tables.
- **Do not invent product facts.** Example strings show a form. A claim about
  what a product does, sends or ships comes from reading that product.
- **Examples and numbers in prose are reference only**; the SVG files and the
  token blocks govern.

## How this repository reaches the docs site

`fundaments-landing` copies `README.md`, `guidelines.md`, `tokens.md`,
`brand/README.md` and this file into `fundaments.work/docs/design-system/`
with `pnpm sync:docs`. Write for that:

- Relative links between these five files are rewritten and checked. A link to
  any other file (`canvas.html`, a neighbouring repo) becomes plain text on the
  site, so do not depend on it for meaning.
- Headings become anchors: lower-case, punctuation removed, spaces to hyphens.
  A section titled `19 · Obsidian plugins` is `#19--obsidian-plugins`. Renaming
  a heading breaks links to it.
- The first `# Title` is dropped and becomes the page title. Do not put anything
  before it.
- The site adds a Brand assets page with downloads and file sizes; do not
  duplicate file sizes here.

## Related repos

- `Theorem/design.md` and `theorem-landing/design.md` are pointers to this
  repository, not independent copies. Do not edit them as if they were.