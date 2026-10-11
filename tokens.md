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
| **Base** | Background, surface, text, hairline, radius, type, tracking, spacing, motion | Never |
| **Accent** | One colour, one meaning | Always |

A product adopts the system by taking the base unchanged and supplying
one accent. Nothing else is negotiable per product.

### Products in scope

| Product | Base | Accent |
|---|---|---|
| **Theorem** | shared (already ships it) | Stone `#c8b89a` |
| **Fundaments.work** | shared | Acid lime `#c6f135` |
| **Lemma** | Obsidian's theme variables | **Out of scope** |
| **Akshar IME** | shared, when it exists | not yet set |

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

### One base

**The system has a single base: dark.** Carbon `#12140f`, on the values
Theorem's app already ships.

```css
:root {
  --bg:         #141416;
  --surface:    #1c1c20;
  --surface-hi: #28282c;
  --line:       #3d3d42;
  --text:       #e8e6e1;
  --text-60:    #9a9a9a;
}
```

Light is a theme inside the system, not a rival to it. A light override
ships alongside; it is not the default and products do not choose
between brands.

**Why dark is the base and not light.** Carbon and Theorem's dark were
already the same palette under two names — background, surface, text and
muted differ by an RGB distance of 2, 4, 6 and 7 respectively, well
inside the gap you would get from rounding. Only the hairline genuinely
diverged (`#282c22` vs `#3d3d42`), and Theorem's is adopted as the shared
value: 1.72:1 on the base, enough for a decorative boundary.

**Why the accent stays per-product.** An accent only works on the base
it was chosen for. Lime `#c6f135` scores 14.16:1 on carbon and **1.24:1
on paper** — unusable on a light surface, the same failure mode as Stone
at 1.85:1. One base, per-product accent. The accent is the only thing a
product gets to choose.

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

Theorem inherits the shared base and chooses Stone as its accent. Its
dark theme already matches the shared base exactly, so the product needs
no migration.

```css
:root {
  --accent:        #c8b89a;   /* stone — reading progress only  */
  --accent-ink:    #1a1a1a;   /* ink set on stone                */

  --hl-thesis:        #fef08a;
  --hl-method:        #bae6fd;
  --hl-fact:          #bbf7d0;
  --hl-quote:         #fed7aa;
  --hl-question:      #e9d5ff;
  --hl-contradiction: #fecdd3;
}
```

> **Accent mechanism.** Theorem's `--app-accent` defaults to `#000000`
> and is user-selectable from eight presets. `computeAccentVariants()`
> derives hover, light and contrast variants at runtime and enforces
> 4.5:1 against the active background. This is the best mechanism in the
> system; other products should copy it rather than hard-code an accent.

### Light theme

Light is an override, not a second brand. Theorem's existing light theme
keeps its values and its name.

```css
.theme-light {
  --app-bg:               #faf9f7;   /* page background */
  --app-surface:          #f4f3f0;   /* panels */
  --app-surface-elevated: #ffffff;
  --app-surface-muted:    #e8e7e2;
  --app-surface-variant:  #e0dfda;
  --app-surface-hover:    #d9d8d3;
  --app-border:           #d4d3ce;   /* hairlines */
  --app-border-subtle:    #e2e1dd;
  --app-text-primary:     #1c1c1c;   /* text, mark */
  --app-text-secondary:   #6b6b6b;   /* secondary text */
  --app-text-muted:       #9c9c9c;   /* never text — see AA */
  --app-text-inverse:     #ffffff;
}
```

### Dark theme

Theorem's dark theme is the shared base. `applyAppTheme()` writes these
at runtime; the values are identical to the shared layer, so this is
recorded for reference rather than as a separate palette.

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

The lab takes the shared base unchanged. It chooses one thing: the accent.

```css
:root {
  --accent:        #c6f135;   /* lime — mark, one action per view  */
  --accent-hover:  #d6ff47;
  --accent-ink:    #293500;   /* ink set on lime                  */
  --recessed:      #0d0f0a;   /* deep carbon, inset panels        */
  --accent-2:      #b3d17a;   /* sage — secondary, used sparingly */
}
```

The base it inherits: `--bg #141416`, `--surface #1c1c20`,
`--text #e8e6e1`, `--line #3d3d42`.

Carbon and lime remain the lab's identity on the web and in every social
frame. Nothing is retired — the values are simply named as slots rather
than as a private palette, so they now sit in the same system as
Theorem's.

**Lime is one signal per frame.** Never two competing lime elements on
one screen. Carbon carries almost everything else.

### The `--line` collision, resolved

The two palettes previously defined `line` differently — `#e5e5e5` for
Theorem's light theme and `#282c22` for the lab. Under one base this is
gone: `--line` is `#3d3d42` everywhere, measured at 1.72:1 on the base
and 1.62:1 on the surface.

Theorem's light theme keeps its own hairline, `#d4d3ce`, inside
`.theme-light`. Light is scoped to a theme block, so it can no longer
collide with another product's tokens on the same page. **The
prefix-by-product workaround is no longer needed.**

---

## State colour

Each product has exactly **one** accent and exactly **one** meaning for
it. It is not decorative and it is never a second accent.

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

Already compliant. Its dark theme is the shared base, so there is nothing
to migrate. Its light theme stays as a theme override.

### Fundaments.work

1. Replace `--font-sans: "Inter"` with DM Sans, and `--font-mono:
   "JetBrains Mono"` with DM Mono.
2. Rebalance the type hierarchy: the current headings run 600–700 at
   −4% to −6%, which the system replaces with weight 300 and −3%.
3. Collapse five easing curves into the shared one, and adopt
   `--duration-fast|normal|slow`.
4. Move off-scale px literals onto the spacing scale.
5. Rename the palette to slot names: `--carbon` → `--bg`, `--bone` →
   `--text`, `--slate` → `--text-60`, `--line` → the shared `#3d3d42`.
   Lime and sage become `--accent` and `--accent-2`.
6. Delete the Inter and JetBrains Mono `@fontsource` dependencies once
   step 1 lands, and regenerate the brand exports in `brand/exports`,
   which are rasterised in Inter today.

The base itself needs no change — the lab is already on carbon, which is
within 2/255 of the shared background.

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

| Shared layer | Base | Radius | Type | Spacing | Motion |
|---|---|---|---|---|---|
| `fundaments-landing` | **near** | adopted | **not adopted** | **not adopted** | **not adopted** |
| `theorem-landing` | **not adopted** | adopted | adopted | **not adopted** | **not adopted** |
| `Theorem` | adopted | adopted | adopted | adopted | adopted |
| `Lemma` | n/a — inherits Obsidian | | | | |

The lab's base is already within 2/255 of the shared background, so its
real gap is typography, spacing and motion. `theorem-landing` is the
outlier: it publishes a light palette that no longer exists in the
system.