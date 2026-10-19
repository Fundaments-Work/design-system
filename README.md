# Fundaments.work Design System

One system for the lab and every product it makes. Square, quiet, and set
in two weights.

These are the defaults. Every product adopts them; none of them is
provisional. They cover everything the lab ships, not only the web: marketing
and docs sites, desktop apps, Obsidian plugins, terminal output and install
scripts, READMEs and repositories, release notes, app icons and installers,
screenshots, charts, forms, email, and a checklist for adding a product.

Read it on the docs site at
[fundaments.work/docs/design-system](https://fundaments.work/docs/design-system/).
It is reference material, not a product.

---

## What's here

| File | What it is |
|---|---|
| [`tokens.md`](./tokens.md) | Token values: shared layer, extended tokens (status colour, type scale, density, syntax, charts, terminal, icons), each product's values, drift and adoption |
| [`guidelines.md`](./guidelines.md) | The language: the core (sections 1–7), the rules for every surface (8–27, ending in the new-product checklist), decisions and adoption (28–29) |
| [`AGENTS.md`](./AGENTS.md) | The non-negotiables and how to edit this repository, for agents and contributors |
| [`brand/`](./brand/README.md) | Official marks, badges and exports, with their known drift |
| [`canvas.html`](./canvas.html) | The same system as a browsable 10-page document — open this one |

### Brand layout

```
brand/
  marks/    8 SVGs — lab aperture, Theorem turnstile, lockups, favicon
  badges/   4 SVGs — Built with, Zero Telemetry, Read on Theorem, Syncs to Obsidian
  exports/  12 raster derivatives — OG, banners, avatars, Theorem social
```

## One base, one accent

**Base** — background, surface, text, hairline, radius, type, tracking,
spacing, motion. Dark. Identical everywhere, never negotiated per
product.

**Accent** — one colour, one meaning: acid lime. No product chooses its own.

| Product | Accent |
|---|---|
| Theorem | Acid lime `#c6f135` — the same accent as the lab |
| Fundaments.work | Acid lime `#c6f135` — mark, one action |
| Manang | Acid lime `#c6f135`, sage `#b3d17a` for math |
| Lemma | **Out of scope** — inherits Obsidian |

Light is a theme inside the system, not a rival to it.

## The short version

- One dark base for every product — `#141416`, never negotiated
- Corner radius is `0`, on every element, without exception
- DM Sans 300/400 for the interface, DM Mono 300/400 for data
- Hierarchy from size and colour, never from extra weights
- One accent for the whole lab, one meaning, always labelled
- One mark height of clear space, for every mark
- The credit line is `Made by Fundaments.work`, DM Mono, 0.35 × wordmark
- No shadows, no gradients, no blur: depth is a tonal step and a hairline
- State is never colour alone; focus is a 2px lime ring
- Where a host owns the pixels (Obsidian, a terminal, GitHub, email) the host
  wins, and the lab keeps its voice and its honest claims

---

## This replaces

These files disagree with each other and with the shipped code. They
become pointers here:

- `Theorem/design.md`
- `theorem-landing/design.md`
- `fundaments-social/01-brand-and-voice.md` (studio typeface section)

Where this document and a codebase disagree, **the codebase is
authoritative** and this file is the bug.