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

## Two layers

**Shared** — radius, hairlines, type families, tracking, spacing, motion.
Identical everywhere, never negotiated per product.

**Values** — ink, paper, line, surface, state colour. Each product supplies
its own.

| Product | Values |
|---|---|
| Theorem | Ink and paper, light and dark |
| Fundaments.work | Carbon and lime |
| Lemma | **Out of scope** — inherits Obsidian |
| Akshar IME | To be set |

## The short version

- Corner radius is `0`, on every element, without exception
- DM Sans 300/400 for the interface, DM Mono 300/400 for data
- Hierarchy from size and colour, never from extra weights
- One state colour per product, one meaning, always labelled
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