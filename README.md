# Fundaments.work Design System

One system for the lab and every product it makes. Square, quiet, and set
in two weights.

These are the defaults. Every product adopts them; none of them is
provisional.

---

## What's here

| File | What it is |
|---|---|
| [`tokens.md`](./tokens.md) | Token values — shared layer, then each product's values |
| [`guidelines.md`](./guidelines.md) | The language: structure, marks, lockup, colour, type, rules, collaboration, decisions |
| [`brand/`](./brand/README.md) | Official marks, badges and exports, with their known drift |
| [`canvas.html`](./canvas.html) | The same system as a browsable 10-page document — open this one |

### Brand layout

```
brand/
  marks/    7 SVGs — lab aperture, Theorem turnstile, lockups, favicon
  badges/   4 SVGs — Built with, Zero Telemetry, Read on Theorem, Syncs to Obsidian
  exports/  12 raster derivatives — OG, banners, avatars, Theorem social
```

## One base, one accent

**Base** — background, surface, text, hairline, radius, type, tracking,
spacing, motion. Dark. Identical everywhere, never negotiated per
product.

**Accent** — one colour, one meaning. The only thing a product chooses.

| Product | Accent |
|---|---|
| Theorem | Stone `#c8b89a` — reading progress |
| Fundaments.work | Acid lime `#c6f135` — mark, one action |
| Lemma | **Out of scope** — inherits Obsidian |

Light is a theme inside the system, not a rival to it.

## The short version

- One dark base for every product — `#141416`, never negotiated
- Corner radius is `0`, on every element, without exception
- DM Sans 300/400 for the interface, DM Mono 300/400 for data
- Hierarchy from size and colour, never from extra weights
- One accent per product, one meaning, always labelled
- One mark height of clear space, for every mark
- The credit line is `Made by Fundaments.work`, DM Mono, 0.35 × wordmark

---

## This replaces

These files disagree with each other and with the shipped code. They
become pointers here:

- `Theorem/design.md`
- `theorem-landing/design.md`
- `Theorem/ds-bundle/guidelines/design.md`
- `fundaments-social/01-brand-and-voice.md` (studio typeface section)

Where this document and a codebase disagree, **the codebase is
authoritative** and this file is the bug.