# Fundaments.work Design System — Tokens

v1.1 · 2026-10-19

v1.1 adds the **Extended tokens** section, written so the rules in
[`guidelines.md`](./guidelines.md) for desktop apps, docs, CLI output, charts
and code have values to point at. Every value in it is either read from shipped
code or marked **new**, and a new value is specified, not adopted, until the
Adoption status table says otherwise.

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
| **Manang** | shared | Acid lime `#c6f135`, sage `#b3d17a` for math |
| **Lemma** | Obsidian's theme variables | **Out of scope** |

**Lemma is deliberately outside the system.** It runs inside someone
else's application and must inherit that application's theme. Its
interface uses Obsidian's variables directly and nothing more. Its
marketing page, if it has one, uses the lab's tokens like any other
Fundaments.work page. This is a decision, not an omission. What Lemma and
any other Obsidian plugin may still take from the system is listed under
[Obsidian plugins](./guidelines.md#19--obsidian-plugins).

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
value: 1.70:1 on the base, enough for a decorative boundary.

**Why there is one accent.** Theorem used to keep Stone `#c8b89a` as a
product accent. That was a second dialect, so it is retired: every product
uses lime. An accent only works on the base it was chosen for. Lime
`#c6f135` scores 14.16:1 on the old carbon `#12140f` (14.05:1 on the base) and **1.24:1 on paper**, so a light
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

## Extended tokens

Added in v1.1. Names used below, all values already in this file: `--text-muted`
`#929292`, `--border-strong` `#6a6a70`, `--hover` `#454549`, `--recessed`
`#0d0f0a`. Names are the ones to use in new code. Where the row says
**shipped**, the value is read from a product that already runs it and the
codebase wins if the two disagree. Where it says **new**, nothing ships it
yet: it is specified here so the first product to need it does not invent a
value of its own.

### Status

| Token | Dark | Light | Contrast | Status |
|---|---|---|---|---|
| `--danger` | `#f08a8a` | `#a3262a` | 7.63:1 on base, 6.09:1 on raised · 6.96:1 on paper | **new** |
| `--focus-ring` | `2px solid var(--accent)` | `2px solid var(--accent)` (olive `#4d6a00`, 5.91:1 on paper) | 14.05:1 on base | shipped on the web; **new** as a token name |

`--danger` is the only hue the system adds, and it is for **errors and
destructive actions only**. It is never a second accent, never decoration, and
it always sits beside an icon and a text label. There is no success or warning
colour: success is the text colour with a check, warning is the text colour
with a `!`, both labelled. `--danger` fails 4.5:1 on the hover surface
(3.96:1), so it is not drawn on a hovered row; the row's text colour takes over
there.

### Surface and text pairings

Measured against the values in this file, so a rule never relies on a pair
nobody checked.

| Text | on base | on surface | on raised | on hover `#454549` |
|---|---|---|---|---|
| Text `#e8e6e1` | 14.75:1 | 13.62:1 | 11.77:1 | 7.65:1 |
| Secondary `#a0a0a0` | 7.04:1 | 6.50:1 | 5.62:1 | **3.65:1** |
| Muted `#929292` | 5.91:1 | 5.46:1 | 4.72:1 | **3.07:1** |
| Lime `#c6f135` | 14.05:1 | 12.97:1 | 11.21:1 | 7.29:1 |
| Sage `#b3d17a` | 10.79:1 | 9.96:1 | 8.61:1 | 5.60:1 |
| Border strong `#6a6a70` | 3.42:1 | 3.16:1 | 2.73:1 | 1.78:1 |
| Line `#3d3d42` | 1.70:1 | 1.57:1 | 1.36:1 | 1.13:1 |

Two consequences, both rules:

- On the hover and selected-row surface only the primary text colour clears
  4.5:1. Secondary and muted text on a hovered row must step up to primary.
- Muted clears 4.5:1 on base, surface and raised, and fails on hover. A
  control boundary on **raised** is below 3:1 (2.73:1), so a bordered control
  on a raised panel needs a lighter boundary than `--border-strong` or no
  border and a tonal step.

Ink on lime is 10.0:1 with `#293500` and 14.05:1 with the base `#141416`;
either is fine, and `--accent-ink` stays `#293500` for the web.

### Type scale

| Role | Size | Line height | Face | Where | Status |
|---|---|---|---|---|---|
| Hero | `clamp(52px, 9.2vw, 152px)` | 0.92 | Sans 300, −3% | Marketing home only | shipped |
| Display | `clamp(44px, 6.4vw, 104px)` | 0.95 | Sans 300, −3% | Marketing | shipped |
| Headline | `clamp(34px, 4.2vw, 64px)` | 1.0 | Sans 300, −3% | Marketing | shipped |
| Lede | `clamp(18px, 1.5vw, 21px)` | 1.5 | Sans 400, secondary | Marketing, 34em measure | shipped |
| Body, docs | 16–18px | 1.6 | Sans 400, −1% | Docs, long text | shipped |
| Dialog title, wordmark | 15px | 1.3 | Sans 300 or 400 | Desktop | shipped |
| Editor, forms | 13px | 1.5 | Sans 400 / Mono 400 | Desktop | shipped |
| UI | 12px | 1.4 | Sans 400 | Desktop | shipped |
| Meta | 11–12px | 1.4 | Mono 400, 0 tracking | Everywhere | shipped |
| Welcome | 28px | 1.1 | Sans 300 | Desktop empty state | shipped |

The smallest text in any product is 11px, and only in DM Mono. Body text on the
web is never below 16px.

Headline tracking is −3% on the shipped site and −2% in the table under
[Type](#type). The shipped value is what runs; see Known drift.

### Mono weights

DM Mono at 400 is the default everywhere, and the one weight the desktop app
ships. 300 is permitted by the system for mono set above 24px (a large number,
a version in a hero); never for text smaller than that.

### Spacing in practice

The scale `4, 8, 12, 16, 24, 32, 48, 64, 96` is the only set of gaps. Page
gutter is 20px, and 40px from 768px up (**shipped**, `.wrap`). Content width is
capped at 1360px on marketing pages and at the 680px reading column in prose
and Zen modes.

### Breakpoints

| Name | From | Used for |
|---|---|---|
| Phone | 0 | One column, 20px gutter |
| Tablet | 768px | 40px gutter, two columns |
| Desktop | 1024px | Full layout |
| Wide | 1360px | Content stops growing |

These are the two Tailwind steps the shipped site uses (`md`, `lg`) plus the
content cap. Capture and test at **375px** and **1440px**.

### Hit targets

| Input | Minimum | Status |
|---|---|---|
| Pointer (desktop, web) | 24 × 24px, WCAG 2.2 AA | **new** as a rule |
| Touch (phone, tablet, Android) | 44 × 44px | **new** as a rule |

An icon button may be drawn smaller than its target; the target is the
clickable area, not the glyph.

### Desktop density

Read from Manang's workbench, the first desktop consumer. These are the
dimensions to start from.

| Part | Size |
|---|---|
| Top bar | 40px |
| Tab strip | 36px |
| Activity bar | 48px, icons only |
| Status bar | 24px |
| Side panel | 200–480px, default 264px |
| Bottom panel | 96–560px |
| Window | 1280 × 820 default, 640 × 480 minimum, no native frame |
| Reading column (Zen) | 680px |

### Component dimensions

Sizes the rules in [`guidelines.md`](./guidelines.md) use. Status says whether
a product already ships it.

| Part | Value | Status |
|---|---|---|
| Web button | 48px high, 15px Sans 300, 22px side padding | shipped |
| Web field | 40px high, 15px text | **new** (the site's field is 14px with 10px padding) |
| Desktop field | 28px high, 13px text | **new** |
| List and tree row, desktop | 24px | **new** |
| Menu row, desktop | 28px | **new** |
| Primary row, desktop | 40px | shipped (top bar) |
| Table cell | `8px 12px`; dense `4px 8px` | shipped; **new** |
| Code block padding | `12px 16px` | **new** |
| Dialog width | 360–560px | **new** |
| Scrim | `rgb(0 0 0 / 0.78)`, no blur | shipped colour; **new** no blur |
| Toast | 320px wide, 6s, bottom end | **new** |
| Tooltip delay | 500ms on hover, none on focus | **new** |
| Success message | 4s | **new** |
| Copy feedback | 2s | **new** |
| Progress rule | 2px accent line | **new** |
| Splitter | 1px line, 6px hit area | **new** |
| Chart line | 2px, square joins | **new** |
| Chart point | 6px square | **new** |
| Collapse a code block | beyond 40 lines | **new** |
| Screenshot weight | under 300 KB where the content allows | **new** |

### Icons

| Property | Value | Status |
|---|---|---|
| Grid | 16 units | shipped |
| Stroke | 1.25 | shipped |
| Caps and joins | butt caps, mitred joins | shipped |
| Shapes | squares, rules, diagonals; no circles | shipped |
| Rendered sizes | 16px in controls, 20px in navigation, 24px in marketing | **new** |
| Colour | `currentColor`; hover is the accent | shipped |

### Syntax colour

Read from the Manang editor theme. Code is mostly one colour on purpose: with
two weights and one accent there is no rainbow to draw.

| Role | Token | Style |
|---|---|---|
| Plain text, keywords, headings | `--text` | regular |
| Strings, numbers | `--text-60` | regular |
| Punctuation, brackets, operators | `--text-60` | regular |
| Comments | `--text-muted` | italic |
| Names, labels, variables, inline code | sage `#b3d17a` | regular |
| Links | `--accent` | underline for URLs |
| Selection, matches | accent at 28–40% over base, or sage at 22% | wash, never solid |

Code sits on the recessed surface `#0d0f0a`. Text on it: 15.45:1 for text,
7.37:1 for secondary, 6.19:1 for muted. Italic is allowed in code comments
and nowhere else in the system.

### Chart colours

| Slot | Value | Use |
|---|---|---|
| `--chart-focus` | `#c6f135` | The one series or point the chart is about |
| `--chart-2` | `#b3d17a` | Second series |
| `--chart-3` | `#e8e6e1` | Third series |
| `--chart-4` | `#a0a0a0` | Fourth series, context |
| `--chart-5` | `#6a6a70` | Fifth series, background |
| `--chart-grid` | `#3d3d42` | Gridlines, 1px |
| `--chart-axis` | `#929292` | Axis labels, DM Mono 11px |

Aliases only: **new** names for values that already exist. Sequential scales
are the accent mixed into the surface: `color-mix(in srgb, #c6f135 N%, #1c1c20)`
with N = 20, 40, 60, 80, 100.

### Terminal output

| Role | Truecolor | 16-colour fallback | Status |
|---|---|---|---|
| Default text | none, the user's theme | none | **new** |
| Muted | SGR 2 (dim) | SGR 2 | **new** |
| Accent, one thing per screen | `38;2;198;241;53` | `92` | **new** |
| Error | `38;2;240;138;138` | `91` | **new** |

Colour is written only when stdout is a TTY, `NO_COLOR` is unset and `TERM`
is not `dumb`. 24-bit colour is written only when `COLORTERM` is `truecolor` or
`24bit`. No background colours, ever.

### Images and social sizes

| Asset | Size | Status |
|---|---|---|
| Open Graph card | 1200 × 630 | shipped (`brand/exports`) |
| GitHub social preview | 1280 × 640, PNG, under 1 MB | **new**, not yet exported |
| X banner | 1500 × 500 | shipped |
| LinkedIn banner | 1584 × 396 | shipped |
| Facebook banner | 820 × 312 | shipped |
| Avatar | 1024, 512, 400 and smaller square steps | shipped |
| Email header | 1200 × 400 at 2×, shown at 600 wide | **new** |
| Screenshot | 1440 wide, 2× | **new** as a rule |

### App icons

| Property | Value | Status |
|---|---|---|
| Master | 1024 × 1024 SVG, square, no corner rounding | **new** as a rule |
| Field | base `#141416`; the lab's own icon keeps carbon `#12140f` until the drift row is closed | shipped |
| Mark | centred, `#e8e6e1`; the lab's aperture in lime | shipped |
| Mark box, as share of canvas width | 33.3% (Theorem), 62.5% (the lab), 50% for any new product | shipped, shipped, **new** |
| Android adaptive foreground | mark box at most 43% of the 108dp layer | **new** |

The 43% figure is computed, not chosen: the aperture's corner sits √2 times
half the box width from the centre, and the adaptive safe circle is 66dp of
108dp, so the box side is at most 0.43 of the canvas.

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
| Lime on Night | 14.05:1 | AAA |
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
gone: `--line` is `#3d3d42` everywhere, measured at 1.70:1 on the base
and 1.57:1 on the surface.

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
6. ✅ Regenerated the brand exports in `brand/exports` from SVG sources in DM Sans; they were still
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

Recorded so it is not rediscovered later. Rows marked **Fixed** are closed; the rest are open.

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
| `brand/marks/theorem-logo.svg` | **Fixed.** Was fill `#0a0a0a`; now `#1c1c1c` |
| `brand/marks/theorem-app-icon.svg` | **Fixed.** Was fill `#0a0a0a` with `rx="100"`; now `#141416` / `#e8e6e1` at radius 0 |
| `brand/badges/fundaments-badge.svg` | **Fixed.** Field was `#1e221b`; now `#0d0f0a`, the recessed step |
| `theorem-landing/brand` page colours | **Fixed.** The page hardcoded hexes and drifted: it documented a `#7a7a7a` "Disabled" grey that is not a token there, and never mentioned `--color-recessed`, which paints several sections. Swatches are now parsed out of `src/styles/global.css` at build time (`src/lib/tokens.ts`), so a token cannot be missing or stale |
| `fundaments-landing`, `Manang` secondary and muted text | Both ship secondary `#9a9a9a` and muted `#7a7a7a` (`--color-text-60` / `--color-text-40`, `--mng-text-60` / `--mng-text-muted`). This file specifies `#a0a0a0` (7.04:1) and `#929292` (5.91:1). `#7a7a7a` is 4.29:1 on the base and Manang already labels it "never text"; the site uses `--color-text-40` for text |
| Contrast numbers measured on carbon | **Fixed in v1.1.** Lime 14.16:1 and line 1.72:1 were measured on `#12140f`. On the base `#141416` they are 14.05:1 and 1.70:1. The guidelines table also listed muted as 6.54:1, which is `#9a9a9a`; the token `#929292` is 5.91:1 |
| `Manang` focus ring | Draws `1px` (`var(--hairline)`); the site draws `2px`. The system now says 2px (see Extended tokens) |
| `Manang` light accent ink | Dark `--mng-accent-ink` is `#141416`; this file and the site use `#293500`. Both clear 4.5:1 on lime (14.05:1 and 10.0:1), so this is a naming split, not a failure |
| `fundaments-landing` headline tracking | Display and headline are both −3% in `global.css`; the Type table says headline is −2% |
| `brand/theorem-brand.zip` | Exists here, is not served by fundaments.work (only `fundaments-brand.zip` is), and its contents have not been checked against `brand/marks` |
| `brand/exports` GitHub social preview | There is no 1280 × 640 export; repositories use the 1200 × 630 card, which GitHub crops |
| `public/brand/fundaments-brand.zip` in `fundaments-landing` | Differs byte for byte from `brand/fundaments-brand.zip` here; the loose files under `public/brand/` match the originals. Nothing checks the zip |
| `fundaments-landing` modal | `.modal` uses `backdrop-filter: blur(6px)` and `.modal-card` a hard `12px 12px 0` shadow. The system has no blur and no shadows; the guidelines now say dialogs have neither |
| `fundaments-landing` docs code colours | The theme draws the code surface and border from tokens, but syntax token colours are Expressive Code's default theme. They should be the roles in Syntax colour |
| `fundaments-landing` spacing | A handful of component paddings still sit off the 4px scale |
| `Lemma/styles.css` | Four hardcoded Tailwind hexes in swipe shadows that contradict the rating colours — Easy swipes blue but rates cyan |
| `Lemma/src/ui/StatsModal.ts` | Chart.js is handed raw `var(--interactive-accent)` strings; canvas cannot resolve `var()`, so charts fall back to defaults |
| `Theorem` highlight labels | Runtime says Important/Key Idea/Interesting/Critical/Action/Beautiful; the system says the six meanings above |
| `fundaments-landing/README.md`, `theorem-landing/README.md` | **Fixed.** Both documented Hugo after the Astro port — wrong generator, wrong output dir (`public` vs `dist`), a Hugo template snippet for the changelog fetch, and `[params.support]` references. Both now describe Astro, `src/site.ts`, and `src/lib/releases.ts` |
| Support channel URLs | **Open.** The `content` repo that held them once was retired in October 2026. Each landing site now owns `data/support-channels.json`, Theorem and Lemma hold literals, and nothing checks them against each other. Every place the Buy Me Momo URL appears is listed in the handbook note `Brand/Support channels` |
| Brand assets in product repos | Not yet centralised. `og-fundaments-1200x630.png`, `og-theorem-1200x630.png` and the favicons are vendored copies of `brand/exports/` and `brand/marks/`; nothing checks them against the originals |

## Adoption status

Specified is not the same as adopted. Current state:

| Shared layer | Base | Radius | Type | Spacing | Motion |
|---|---|---|---|---|---|
| `fundaments-landing` | adopted | adopted | adopted | partial | adopted |
| `theorem-landing` | adopted | adopted | adopted | adopted | adopted |
| `Theorem` | adopted | adopted | adopted | adopted | adopted |
| `Lemma` | n/a — inherits Obsidian | | | | |
| `Manang` | partial: base adopted, secondary and muted text off-token | adopted | adopted | not checked | adopted |
| `akshar-playground` | adopted | adopted | adopted | partial | adopted |
| `nepali-wordle` | adopted (both themes) | adopted | adopted | adopted | adopted |

Every product now runs the shared base, DM Sans/Mono at two weights,
radius 0, and the shared motion tokens. Spacing is the one gap: the
scale is declared but a few component paddings still sit off it.

### Extended tokens

Everything in [Extended tokens](#extended-tokens) marked **new** is specified
and adopted nowhere. Items marked **shipped** are adopted where they were read
from: the type scale and spacing on `fundaments-landing`, density, icons and
syntax colour on `Manang`.

| New token or rule | Adopted by |
|---|---|
| `--danger` | nobody |
| `--focus-ring` as a named token | nobody; `fundaments-landing` and `Manang` draw the same outline by hand |
| `--chart-*` aliases | nobody |
| Terminal colour rules | nobody; `Manang`'s `install-linux.sh` prints plain text and sets no colour |
| GitHub social preview, email header | no export exists |
