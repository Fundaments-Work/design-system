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
| **Accent** | One colour, one meaning | Never. The lab has one accent: acid lime |

A product adopts the system by taking the base and the accent unchanged.
Nothing is negotiable per product, and no product keeps a palette of its
own.

### Products in scope

| Product | Base | Accent |
|---|---|---|
| **Theorem** | shared | Acid lime `#c6f135` |
| **Fundaments.work** | shared | Acid lime `#c6f135` |
| **Lemma** | Obsidian's theme variables | **Out of scope** |

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
  --text-60:    #a0a0a0;
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

**Why there is one accent.** Theorem used to keep Stone `#c8b89a` as a
product accent. That was a second dialect, so it is retired: every product
uses lime. An accent only works on the base it was chosen for. Lime
`#c6f135` scores 14.16:1 on carbon and **1.24:1 on paper**, so a light
theme sets the accent in a dark olive (`#4d6a00`) and never in lime.

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

Theorem takes the shared base and the shared accent unchanged. It adds
only the six highlight colours, which are content.

```css
:root {
  --accent:        #c6f135;   /* lime — the one signal per frame */
  --accent-ink:    #293500;   /* ink set on lime                 */

  --hl-thesis:        #fef08a;
  --hl-method:        #bae6fd;
  --hl-fact:          #bbf7d0;
  --hl-quote:         #fed7aa;
  --hl-question:      #e9d5ff;
  --hl-contradiction: #fecdd3;
}
```

> **Accent mechanism.** Theorem's `--app-accent` defaults to lime
> `#c6f135`. The user can still pick another from the settings presets.
> `computeAccentVariants()` derives hover, light and contrast variants at
> runtime and enforces 4.5:1 against the active background. This is the
> best mechanism in the system; other products should copy it rather than
> hard-code an accent.

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
  --app-text-secondary:   #5c5c5c;   /* secondary text, 6.4:1 on paper */
  --app-text-muted:       #666666;   /* tertiary text, 5.5:1 on paper */
  --app-text-disabled:    #9c9c9c;   /* disabled only — fails AA */
  --app-border-strong:    #8c8c88;   /* form-control boundary, 3.2:1 */
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
  --app-text-secondary:   #a0a0a0;   /* secondary text, 7.0:1 */
  --app-text-muted:       #929292;   /* tertiary text, 5.9:1 */
  --app-text-disabled:    #7a7a7a;   /* disabled only — 4.3:1 */
  --app-border-strong:    #6a6a70;   /* form-control boundary, 3.4:1 */
  --app-text-inverse:     #141416;
}
```

The accent is derived per theme: lime on dark, a dark olive on light.

### Contrast

Recomputed against these values, not the marketing page's greys.

| Pair | Ratio | |
|---|---|---|
| Ink on Paper | 16.20:1 | AAA |
| Ink 60 on Paper | 6.36:1 | AA |
| Ink muted on Paper | 5.46:1 | AA |
| Ink disabled on Paper | **2.61:1** | **Fails AA** |
| Dark text on Night | 14.75:1 | AAA |
| Dark secondary on Night | 7.04:1 | AAA |
| Dark muted on Night | 5.91:1 | AA |
| Dark disabled on Night | **4.29:1** | **Fails AA** |
| Control border on Night | 3.42:1 | 3:1 for UI |
| Control border on Paper | 3.21:1 | 3:1 for UI |
| Lime on Night | 14.16:1 | AAA |
| **Lime on Paper** | **1.24:1** | **Fails AA** |

Two rules follow, and both are enforced in the code:

**Disabled is never text a reader needs.** `--app-text-disabled` is for
disabled states and decorative rules only. Secondary and muted text were
raised to clear 4.5:1 on every surface, because the apps use muted as real
text in about 300 places. Form-control boundaries use `--app-border-strong`
(3:1); the 1.7:1 hairline is decorative and never the only cue for a
control.

**Lime is never text on a light surface.** At 1.24:1 it fails outright.
On light, the accent is set in dark olive, and wherever it appears it
carries a DM Mono label beside it.

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

The lab has exactly **one** accent and exactly **one** meaning for it:
the one signal per frame. It marks where you are (the open item's edge,
the focus ring, the selection), the progress, or the single action. It is
not decorative and it is never a second accent.

- **Theorem** and **Fundaments.work** — Acid lime `#c6f135`.
- **Lemma** — none in-app. Obsidian owns its accent.

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

### Highlight washes

**A highlight is never a solid fill behind base-coloured text.** These
colours are pale and saturated, so a solid one behind the base text
colour scores **1.07:1** — effectively invisible. Measured on
`theorem-landing`, where three separate components had the same defect.

```css
/* Dark base — wash toward the highlight */
--hl-thesis-wash: color-mix(in srgb, #fef08a 30%, transparent);

/* Light base — wash toward ink */
--hl-thesis-wash: color-mix(in srgb, #141416 20%, transparent);
```

| | Wash | Text | Ratio |
|---|---|---|---|
| Dark | 30% highlight over base | `--color-text-strong` | 7.43:1 |
| Light | 20% ink over base | `--color-text` | 10.52:1 |

**Light washes toward ink, not toward the colour.** A 30% yellow wash
over paper measures 1.04:1 against the base — on light the highlight
would be *invisible* rather than illegible, which is the worse failure.

Swatch buttons keep the **full** colour, so the six stay distinguishable
as chips. The wash is only what sits behind running text.

### Text selection

Selection has the same constraint and gets its own tokens, because it
must read as a block rather than a tint.

| | Background | Ink | Ratio |
|---|---|---|---|
| Dark | 40% highlight over base | `--color-text-strong` | 5.32:1 |
| Light | solid `#fef08a` | `#1c1c1c` | 14.64:1 |

Light keeps a solid highlight because ink on yellow is strong; dark
cannot, since white text on a pale fill is what fails.

---

## How a product adopts this

No build step is required. Read the values above and apply them.

### Theorem

**Done.** One base, one accent: dark is the default, lime is the default
accent, weights are 300 and 400, DM Sans and DM Mono ship with the app, and
the sidebar is a fixed rail. The reader keeps its serif for book content,
which is content and not interface. Its own UI kit and guidelines are
retired.

### Fundaments.work

**Done.** Adopted in `fundaments-landing`.

1. ✅ Replaced Inter and JetBrains Mono with DM Sans and DM Mono.
2. ✅ Rebalanced the type hierarchy: headings were 600–700 at −4% to −6%,
   now 300 at −3%, with 400 for body.
3. ✅ Collapsed five easing curves into the shared one with the three
   standard durations.
4. ✅ Renamed the palette to slot names. Lime and sage became `--accent`
   and `--accent-2`.
5. ✅ Removed the unused `@fontsource` dependencies and stopped shipping
   the two variable font files.
6. ⬜ Regenerate the brand exports in `brand/exports`, which are still
   rasterised in Inter.
7. ⬜ Off-scale px literals remain — the scale is adopted in the tokens but
   a handful of component paddings still sit outside it.

The base itself needed no change — the lab was already on carbon, within
2/255 of the shared background.

### theorem-landing

**Done.** Adopted in `theorem-landing`: shared base, DM Sans/DM Mono, two
weights, shared motion tokens, the lab's lime accent, and the highlight and
selection fixes below.

### Lemma

Nothing. It inherits Obsidian's tokens. Its landing page, if any, uses the
Fundaments.work values above like any other lab page.

### Theorem — pointers

`design.md` in Theorem and in `theorem-landing` are pointers to this
repository. Theorem's `ds-bundle/` UI kit is retired.

---

## Known drift

Recorded so it is not rediscovered later. None of it is fixed yet.

| Where | Issue |
|---|---|
| `theorem-landing` highlight + selection | **Fixed.** Pale solid fills behind base text scored 1.07:1; now translucent washes. See Highlight washes |
| `theorem-landing` focus ring | **Fixed.** `--color-text` is 1.19:1 on light paper. Now a `--focus-ring` token that inverts per theme |
| `theorem-landing` `color-scheme` | **Fixed.** Declared `light` while the page is dark |
| `fundaments-landing` palette + type + motion | **Fixed.** Adopted the shared base, DM Sans/Mono, two weights, shared motion |
| `Theorem/design.md`, `theorem-landing/design.md` | **Fixed.** Both are pointers to this repository now. `Theorem/ds-bundle/guidelines/design.md` is gitignored and regenerates from `Theorem/design.md` |
| `fundaments-social/01-brand-and-voice.md` | **Fixed.** Typeface section updated to DM Sans/DM Mono |
| `brand/exports/*.png` | Still rasterised in Inter. Regenerate from the DM Sans lockup |
| `brand/marks/favicon.svg`, `fundaments-logo.svg`, `fundaments-lockup.svg`, `fundaments-mark-carbon.svg` | Their field is Carbon `#12140f`, which no longer matches any token. The base is `#141416` and the recessed step is `#0d0f0a`. Found while vendoring these files into nepali-wordle; the files themselves are otherwise canonical |
| `brand/exports/avatar-*.png`, `banner-*.png` | Same Inter rasterisation as above |
| `brand/marks/theorem-logo.svg` | Fill `#0a0a0a`; the token is `#1c1c1c` |
| `brand/marks/theorem-app-icon.svg` | Fill `#0a0a0a`, and `rx="100"` — the only rounded corner in the brand kit |
| `brand/badges/fundaments-badge.svg` | Field `#1e221b`; no token matches it (nearest is `#1e201b`) |
| `fundaments-landing` spacing | A handful of component paddings still sit off the 4px scale |
| `Lemma/styles.css` | Four hardcoded Tailwind hexes in swipe shadows that contradict the rating colours — Easy swipes blue but rates cyan |
| `Lemma/src/ui/StatsModal.ts` | Chart.js is handed raw `var(--interactive-accent)` strings; canvas cannot resolve `var()`, so charts fall back to defaults |
| `Theorem` highlight labels | Runtime says Important/Key Idea/Interesting/Critical/Action/Beautiful; the system says the six meanings above |
| `fundaments-landing/README.md`, `theorem-landing/README.md` | **Fixed.** Both documented Hugo after the Astro port — wrong generator, wrong output dir (`public` vs `dist`), a Hugo template snippet for the changelog fetch, and `[params.support]` references. Both now describe Astro, `src/site.ts`, and `src/lib/releases.ts` |
| Support channel URLs | **Fixed.** The Buy Me Momo URL was written out in six places. They now live once in [`Fundaments-Work/content`](https://github.com/Fundaments-Work/content) → `support.json`; the landing sites generate from it, and Theorem and Lemma hold a literal guarded by `pnpm check:content` |
| Brand assets in product repos | Not yet centralised. `og-fundaments-1200x630.png`, `og-theorem-1200x630.png` and the favicons are vendored copies of `brand/exports/` and `brand/marks/`; nothing checks them against the originals |

## Adoption status

Specified is not the same as adopted. Current state:

| Shared layer | Base | Radius | Type | Spacing | Motion |
|---|---|---|---|---|---|
| `fundaments-landing` | adopted | adopted | adopted | partial | adopted |
| `theorem-landing` | adopted | adopted | adopted | adopted | adopted |
| `Theorem` | adopted | adopted | adopted | adopted | adopted |
| `Lemma` | n/a — inherits Obsidian | | | | |
| `akshar-playground` | adopted | adopted | adopted | partial | adopted |
| `nepali-wordle` | adopted (both themes) | adopted | adopted | adopted | adopted |

Every product now runs the shared base, DM Sans/Mono at two weights,
radius 0, and the shared motion tokens. Spacing is the one gap: the
scale is declared but a few component paddings still sit off it.