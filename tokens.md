# Fundaments.work Design System — Tokens

v1.0 · 2026-10-11

> **Status.** These are the defaults. Where this document and a shipped
> codebase disagree, the codebase is authoritative and this file is the bug.
> Theorem's `src/core/styles/design-tokens.css` and
> `src/core/lib/design-tokens.ts` are the reference implementation.

---

## How the system is layered

Two layers, and the split is the whole idea:

| Layer | Contains | Varies by product? |
|---|---|---|
| **Shared** | Radius, hairlines, type families, tracking, spacing, motion | Never |
| **Values** | Ink, paper, line, surface, state colour | Always |

A product adopts the system by taking the shared layer unchanged and
supplying its own values. Nothing else is negotiable per product.

### Products in scope

| Product | Values from | Status |
|---|---|---|
| **Theorem** | Its own tokens | Reference implementation |
| **Fundaments.work** (lab site) | Carbon and lime | Keeps its own palette |
| **Lemma** | Obsidian's theme variables | **Out of scope — inherits Obsidian** |
| **Akshar IME** | To be set | Follows the system when it exists |

**Lemma is deliberately outside the system.** It runs inside someone
else's application and must inherit that application's theme. Its
interface uses Obsidian's variables directly and nothing more. Its
marketing page, if it has one, uses the lab's tokens like any other
Fundaments.work page. This is a decision, not an omission.

---

## Shared layer

```css
:root {
  --radius: 0;
  --hairline: 1px;

  --font-sans: "DM Sans", sans-serif;   /* 300, 400 only */
  --font-mono: "DM Mono", monospace;     /* 300, 400 only */

  --tracking-display: -0.03em;
  --tracking-headline: -0.02em;
  --tracking-body:     -0.01em;
}
```

### Radius

`0`, on every element, without exception. No rounded rectangles, no pills,
no circles on controls. This is the system's most visible invariant and
Theorem enforces it in CSS as a backstop, overriding any `rounded-*`
utility that reaches a component by accident.

### Dividers

`1px`, drawn in the product's Line colour. Depth comes from hairlines and
surface steps, never from shadows. Theorem keeps `--shadow-*` tokens for
the reader and platform surfaces only; it is not part of the UI language.

### Type

Two families, two weights each. No other weight is used anywhere.

- **DM Sans** — interface and running text. 300 and 400.
- **DM Mono** — anything that is data: versions, sizes, counts,
  timestamps, file names, citations. 300 and 400.

Hierarchy comes from size and colour, never from extra weights. Heading
tracking tightens as size grows.

| Role | Face | Tracking |
|---|---|---|
| Display | Sans 300 | −3% |
| Headline | Sans 300 | −2% |
| Body | Sans 400 | −1% |
| Metadata | Mono 400 | 0 |

### Spacing

Base unit 4px. The permitted scale is `4, 8, 12, 16, 24, 32, 48, 64, 96`.
No arbitrary values.

### Motion

Durations come from Theorem's `--duration-*`: `fast 150ms`,
`normal 220ms`, `slow 320ms`, on `cubic-bezier(0.22, 1, 0.36, 1)`.

No bounce, no spring, no elastic. Motion confirms that state changed; it
never decorates.

---

## Values — Theorem

These are what Theorem's app **actually ships**, read from
`design-tokens.ts` and `design-tokens.css`. Theorem runs a warm neutral
palette — not the pure greys its marketing pages use. The app is what
users see, so the app is canonical; see [Known drift](#known-drift).

```css
:root {
  --ink:      #1c1c1c;   /* text, mark, buttons      */
  --ink-60:   #6b6b6b;   /* secondary text           */
  --ink-muted:#9c9c9c;   /* tertiary text — see AA   */
  --line:     #d4d3ce;   /* hairlines                */
  --line-soft:#e2e1dd;   /* dividers inside a panel  */
  --surface:  #f4f3f0;   /* panels                   */
  --surface-hi:#e8e7e2;  /* hover                    */
  --paper:    #faf9f7;   /* page background          */
  --stone:    #c8b89a;   /* state only               */

  --hl-thesis:        #fef08a;
  --hl-method:        #bae6fd;
  --hl-fact:          #bbf7d0;
  --hl-quote:         #fed7aa;
  --hl-question:      #e9d5ff;
  --hl-contradiction: #fecdd3;
}
```

> **Accent.** Theorem's `--app-accent` defaults to `#000000` and is
> user-selectable from eight presets. `computeAccentVariants()` derives
> hover, light and contrast variants at runtime and enforces 4.5:1 against
> the active background. This is the best mechanism in the system; other
> products should copy it rather than hard-code an accent.

### Dark theme

Theorem ships a dark theme, applied by `applyAppTheme()`. These are the
canonical dark values; any earlier proposal that differed has been
discarded.

```css
.theme-dark {
  --app-bg:               #141416;   /* page background */
  --app-surface:          #1c1c20;   /* panels */
  --app-surface-elevated: #28282c;   /* raised panels */
  --app-surface-muted:    #353539;
  --app-surface-variant:  #3d3d42;
  --app-surface-hover:    #454549;   /* hover */
  --app-border:           #3d3d42;   /* hairlines */
  --app-border-subtle:    #323236;
  --app-text-primary:     #e8e6e1;   /* text, mark */
  --app-text-secondary:   #9a9a9a;   /* secondary text */
  --app-text-muted:       #7a7a7a;   /* tertiary text */
  --app-text-inverse:     #141416;
}
```

Stone is the same in both themes.

### Contrast

Recomputed against these values, not the marketing page's greys.

| Pair | Ratio | |
|---|---|---|
| Ink on Paper | 16.20:1 | AAA |
| Ink 60 on Paper | 5.06:1 | AA |
| Ink muted on Paper | **2.61:1** | **Fails AA** |
| Dark text on Night | 14.75:1 | AAA |
| Dark muted on Night | 6.54:1 | AA |
| Stone on Night | 9.44:1 | AAA |
| **Stone on Paper** | **1.85:1** | **Fails AA** |

Two rules follow, and both are enforced in the code:

**Ink muted is never text.** At 2.61:1 it cannot carry meaning. It is for
disabled states and decorative rules only. Theorem's own components use
`--app-text-secondary` for anything a reader must be able to read.

**Stone is never text on a light surface.** At 1.85:1 it fails outright.
Wherever Stone appears it carries a DM Mono label beside it.

---

## Values — Fundaments.work

The lab keeps its own palette. Carbon and lime are its identity on the
web and in every social frame, and they are not being retired.

```css
:root {
  --carbon:      #12140f;   /* background */
  --carbon-deep: #0d0f0a;   /* recessed sections */
  --line:        #282c22;   /* hairlines */
  --lime:        #c6f135;   /* mark, one action per view */
  --sage:        #b3d17a;   /* secondary accent, sparing */
  --bone:        #e3e3da;   /* text */
  --slate:       #9ca190;   /* muted text */
}
```

It takes the shared layer unchanged: radius 0, hairlines, DM Sans and
DM Mono, the spacing scale, the motion durations.

**Lime is one signal per frame.** Never two competing lime elements on
one screen. Carbon carries almost everything else.

### Name collision

Both palettes define a `line` token with different values — `#e5e5e5` on
Theorem, `#282c22` on the lab. **If both ever load on one page, prefix
each by product:** `--theorem-line`, `--fundaments-line`. This is not
hypothetical; the two sites share a build lineage.

---

## Name collision: `--line`

| Context | Token | Value |
|---|---|---|
| Theorem | `--line` | `#e5e5e5` |
| Fundaments.work | `--line` | `#282c22` |

Prefix by product when they meet. Do not redefine one in terms of the
other.

---

## State colour

Each product has exactly **one** state colour and exactly **one** meaning.
It is not decorative and it is never a second accent.

- **Theorem** — Stone `#c8b89a`, reading progress only.
- **Fundaments.work** — Acid lime `#c6f135`, the mark and one action per
  view.
- **Lemma** — none in-app. Obsidian owns its accent.
- **Akshar IME** — not yet set.

State colour is always paired with a text label. Never state by colour
alone.

---

## Highlight taxonomy

Theorem's six highlight colours each carry one fixed meaning, so exported
notes stay consistent wherever they are read. Meaning is part of the
colour: do not swap them, and do not use them decoratively.

| Meaning | Colour |
|---|---|
| Core thesis | Yellow `#fef08a` |
| Method | Blue `#bae6fd` |
| Agreement or fact | Green `#bbf7d0` |
| Quote | Orange `#fed7aa` |
| Question | Purple `#e9d5ff` |
| Contradiction | Red `#fecdd3` |

> **Open.** Theorem's runtime labels these differently — Important, Key
> Idea, Interesting, Critical, Action, Beautiful — in
> `design-tokens.ts`. The six colours are identical; the labels are not.
> This needs one canonical answer before the tokens ship.

---

## How a product adopts this

No build step is required. Read the values above and apply them.

### Theorem

Already compliant. Its token names are the system's names. No migration.

### Fundaments.work

1. Replace `--font-sans: "Inter"` with DM Sans, and `--font-mono:
   "JetBrains Mono"` with DM Mono.
2. Rebalance the type hierarchy: the current headings run 600–700 at
   −4% to −6%, which the system replaces with weight 300 and −3%.
3. Delete the Inter and JetBrains Mono `@fontsource` dependencies once
   step 1 lands, and regenerate the brand exports in `brand/exports`,
   which are rasterised in Inter today.

### Lemma

Nothing. It inherits Obsidian's tokens. Its landing page, if any, uses the
Fundaments.work values above like any other lab page.

### Theorem — pointers

`design.md` in Theorem, in `theorem-landing`, and in `ds-bundle/guidelines/`
are three revisions of the same document that disagree. Replace all three
with a pointer to this repository.

---

## Known drift

Recorded so it is not rediscovered later. None of it is fixed yet.

| Where | Issue |
|---|---|
| `theorem-landing/src/styles/global.css` | Uses neutral greys `#1a1a1a` / `#e5e5e5` / `#ffffff`; the app ships warm `#1c1c1c` / `#d4d3ce` / `#faf9f7`. Two palettes for one product — the marketing pages are the outlier, not the app |
| `theorem-landing` `design.md`, `Theorem/design.md`, `Theorem/ds-bundle/guidelines/design.md` | Three revisions of one document, disagreeing on fonts, motion and ink |
| `brand/marks/theorem-logo.svg` | Fill `#0a0a0a`; the token is `#1c1c1c` |
| `brand/marks/theorem-app-icon.svg` | Fill `#0a0a0a`, mark `#fafaf8`, and `rx="100"` — the only rounded corner in the brand kit |
| `brand/badges/fundaments-badge.svg` | Field `#1e221b`; no token matches it (nearest is `#1e201b`) |
| `fundaments-landing/src/styles/global.css` | Still Inter + JetBrains Mono at weights 600–650. No `--duration-*` tokens; five separate easing curves; roughly half its px literals are off the spacing scale |
| `Lemma/styles.css` | Four hardcoded Tailwind hexes in swipe shadows that contradict the rating colours — Easy swipes blue but rates cyan |
| `Lemma/src/ui/StatsModal.ts` | Chart.js is handed raw `var(--interactive-accent)` strings; canvas cannot resolve `var()`, so charts fall back to defaults |
| `fundaments-landing/README.md`, `theorem-landing/README.md` | Document Hugo; both projects are Astro |

## Adoption status

Specified is not the same as adopted. Current state:

| Shared layer | Radius | Type | Spacing | Motion |
|---|---|---|---|---|
| `fundaments-landing` | adopted | **not adopted** | **not adopted** | **not adopted** |
| `theorem-landing` | adopted | adopted | **not adopted** | **not adopted** |
| `Theorem` | adopted | adopted | adopted | adopted |
| `Lemma` | n/a — inherits Obsidian | | | |

Radius is the only rule every surface currently follows.