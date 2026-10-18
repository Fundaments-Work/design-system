# design-system — Agent Guide

## What this is

The studio-wide visual and verbal language. Documentation and assets only — no
build, no dependencies, no site.

| File | What it is |
| :--- | :--- |
| [`tokens.md`](./tokens.md) | Token values: shared layer, then the product values, then known drift |
| [`guidelines.md`](./guidelines.md) | The language: structure, marks, lockup, colour, type, rules, collaboration, decisions, adoption |
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
| fundaments-landing | acid lime `#c6f135` | Studio site |
| theorem-landing | acid lime `#c6f135` | Adopts the shared base |
| Lemma | **out of scope** | Runs inside Obsidian and must inherit its theme |

**Lemma is outside the system by decision, not omission.** Do not "fix" it by
pulling lab tokens into the plugin UI. Its published surfaces (README, badge,
release notes) still follow the lab's rules.

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

## Related repos

- [`Fundaments-Work/content`](../content) — shared machine-readable facts across
  products (support channels today). Unrelated to visual design; do not put
  tokens there.
- `Theorem/ds-bundle/` — the packaged TheoremUI React kit. Produced by
  Theorem's own `.ds-sync/` pipeline (DesignSync-driven, agent-graded). Its
  verdict schema v2 is a CI contract: **additive changes only**.
- `Theorem/design.md` and `theorem-landing/design.md` are pointers to this
  repository, not independent copies. Do not edit them as if they were.