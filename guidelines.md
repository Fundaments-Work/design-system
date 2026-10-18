# Fundaments.work Design System — Guidelines

v1.0 · 2026-10-11

One system for the lab and every product it makes. Square, quiet, and set
in two weights. Token values live in [`tokens.md`](./tokens.md); this
document is the language around them.

> **Status.** These are the defaults, not proposals. They replace the
> conflicting `design.md` files in `Theorem`, `theorem-landing` and
> `Theorem/ds-bundle/guidelines/`, and the brand rules in
> `fundaments-social/01-brand-and-voice.md`. Those files become pointers
> here.

---

## 1 · Structure

Fundaments.work is the lab. One system is shared by every app, and each
product chooses only its mark, one state colour and its name.

### Shared by everything

- Zero corner radius
- Hairline dividers
- DM Sans, 300 and 400
- DM Mono for metadata
- Marks on a 24-unit grid
- One credit line

### Products choose

| Product | Descriptor | State colour | Default theme |
|---|---|---|---|
| Fundaments.work | The lab | Acid lime | Dark (Carbon) |
| Theorem | Reading | Acid lime | Dark |
| Lemma | Flashcards, spaced repetition | None in-app — Obsidian owns it | Inherits Obsidian |

The lab site keeps carbon, lime and the system. That question is settled:
the lab's palette is a value set, and the system is the layer above it.

---

## 2 · Marks

Drawn from geometry. Theorem is rectangles on a 24-unit grid. The lab's
aperture is two brackets and a point on a 512 grid. Corner radius is 0 for
both, and no mark is typed, rotated, skewed or outlined.

- **Theorem** — bar 16 × 4, stem 4 × 8, foot 4 × 4. The foot is the
  square that closes a proof.
- **Fundaments.work** — aperture, 512 grid, spine 52, arm 112, nucleus
  r 44. The official SVG governs; the values here are for reference.

### Clear space

One mark height on every side, for every mark. This is the same rule for
the lab and every product.

### Minimum size

14px, taken from Theorem and applied to every mark.

### Mark alone

Use the mark without a wordmark where space is tight: favicons, tabs,
docks and app icons. Ship two colourways — ink on paper, and reversed.

---

## 3 · Lockup and names

Every product carries the lab's name beneath its own, set the same way
each time.

- **Wordmark** — DM Sans Light. Never bold, never italic.
- **Credit** — DM Mono 400, at 0.35 × the wordmark, never below 10px.
- **Credit colour** — the muted text token.

### Where the credit appears

| Place | Treatment |
|---|---|
| Header and hero | Full lockup |
| Footer | One linked sentence: *Made by* Fundaments.work |
| Tab, dock, app icon | Mark alone |

### Names

| Use | Write | Never write |
|---|---|---|
| The lab | Fundaments.work | Fundaments, Fundaments Work, Fundaments Lab |
| Describing it | an independent lab | studio, agency, company |
| Products | Theorem, Lemma | Theorem App |
| Credit sentence | Made by Fundaments.work | Made by Fundaments |

---

## 4 · Colour

Ink and paper carry everything. Lime reports state only. The six
highlight colours each carry one meaning, so exported notes stay
consistent.

### One base, dark

Every product shares one base. Products choose an accent, never a
palette.

| Token | Value | Role |
|---|---|---|
| Background | `#141416` | Page background |
| Surface | `#1c1c20` | Panels |
| Surface raised | `#28282c` | Raised panels |
| Hover | `#454549` | Hover |
| Line | `#3d3d42` | Hairlines |
| Text | `#e8e6e1` | Text, mark |
| Secondary | `#a0a0a0` | Secondary text, 7.0:1 |
| Muted | `#929292` | Tertiary text, 5.9:1 |

### Light theme

Light is a theme inside the system, not a second brand. Theorem's
override keeps its warm neutral.

| Token | Value | Role |
|---|---|---|
| Paper | `#faf9f7` | Page background |
| Surface | `#f4f3f0` | Panels |
| Line | `#d4d3ce` | Hairlines |
| Ink | `#1c1c1c` | Text, mark |
| Ink 60 | `#5c5c5c` | Secondary text, 6.4:1 |
| Ink muted | `#666666` | Tertiary text, 5.5:1 |
| Ink disabled | `#9c9c9c` | Disabled only — fails AA |

### Accent

| Product | Accent | Meaning |
|---|---|---|
| Theorem | Acid lime `#c6f135` | One signal per frame |
| Fundaments.work | Acid lime `#c6f135` | One signal per frame: the mark, the open item, the single action |
| Lemma | none | Obsidian owns it |

### Highlight taxonomy

| Meaning | Colour |
|---|---|
| Core thesis | Yellow `#fef08a` |
| Method | Blue `#bae6fd` |
| Agreement or fact | Green `#bbf7d0` |
| Quote | Orange `#fed7aa` |
| Question | Purple `#e9d5ff` |
| Contradiction | Red `#fecdd3` |

### Contrast

| Pair | Ratio | |
|---|---|---|
| Text on base | 14.75:1 | AAA |
| Muted on base | 6.54:1 | AA |
| **Lime on base** | **14.16:1** | AAA |
| Line on base | 1.72:1 | decorative |
| Ink on Paper | 16.20:1 | AAA |
| Ink 60 on Paper | 6.36:1 | AA |
| Ink muted on Paper | 5.46:1 | AA |
| Ink disabled on Paper | 2.61:1 | **Fails AA** |
| **Lime on Paper** | **1.24:1** | **Fails AA** |

Three rules, all load-bearing:

**The accent never crosses onto the light base.** Lime scores 1.24:1 on
paper. A light theme must use an accent chosen for it, a dark olive, or
none.

**Disabled is never readable text.** It cannot carry meaning at 2.61:1.
Secondary and muted both clear 4.5:1 on every surface. Control boundaries
use the strong border at 3:1, not the decorative hairline.

**Lime is never body text.** On the base it passes; it still always carries
a mono label, because state is never colour alone.

### Fundaments.work

Carbon `#12140f`, deep `#0d0f0a`, line `#282c22`, lime `#c6f135`,
sage `#b3d17a`, bone `#e3e3da`, slate `#9ca190`. Lime is one signal per
frame; carbon carries almost everything.

---

## 5 · Type

Two families, two weights. DM Sans for reading the interface, DM Mono for
anything that is data. Hierarchy comes from size and colour, never from
extra weights.

| Role | Face | Example |
|---|---|---|
| Display | Sans 300 · −3% | A quiet place to read |
| Headline | Sans 300 · −2% | Notes stay in plain Markdown |
| Body | Sans 400 · −1% | Theorem keeps books, papers and feeds on your device. |
| Metadata | Mono 400 | v1.5.8 · EPUB · 318 pp |

---

## 6 · Rules

Short enough to remember.

### Do

- Use the mark alone where space is tight
- Set the wordmark in Light, every time
- Keep one mark height of clear space
- Set every piece of metadata in DM Mono
- Use the state colour for state, with a label
- Repeat the credit line unchanged

### Don't

- Round any corner, anywhere
- Rotate, skew or outline the mark
- Bold the wordmark; use size instead
- Use lime for anything but state, or two lime signals in one frame
- Give an icon button a box or a hover background; it is a bare icon, and hover is the accent colour
- Place a mark on gradients, photos or shadows
- Type a mark as characters; use the SVG

---

## 7 · Collaboration

For contributors, plugin authors, writers and forks.

### Allowed without asking

- Name the lab and its products, with the correct casing
- Use the official badges in READMEs and plugin pages
- Use an unmodified mark to link to its product
- Screenshot the apps in articles, with an accurate caption
- Say "for Theorem" or "Works with Theorem" for compatible work

### Ask first

- A mark inside your product name, logo, icon or domain
- Co-branded lockups, merchandise and print
- Recolouring or altering a mark; the answer is normally no
- Wording that suggests the lab endorses or maintains your work

### Not permitted

- Names like "Theorem X" or "Fundaments X" for third-party work
- Recreating a mark by hand, with characters or with generative tools
- The Zero Telemetry badge on a project that sends telemetry
- Marks on gradients, photos or shadows, or rotated, skewed or outlined

### Badges

*Built with Fundaments.work* · *Zero Telemetry* · *Read on Theorem* ·
*Syncs to Obsidian*.

Layouts only; use the official SVG files. The Obsidian badge names a third
party, so follow Obsidian's own terms beyond it.

### Co-branding

Marks stay separate, with one mark height between them and equal visual
weight. Ours is in a single colour. State the relationship in words, as in
"Built with Fundaments.work".

### Forks

1. The code is open and may be forked
2. The fork takes its own name, mark and palette
3. It removes the marks and the credit line

Plain text such as "Based on Theorem" is fine.

### Proposing a new tool

A tool made with the lab should run fully offline with no server
dependency, send no telemetry, and store data in open formats such as
Markdown or SQLite. Use the contact page on fundaments.work: name the use
and where it will appear, and attach a mock-up if a mark is involved.

---

## 8 · Decisions

Settled. Recorded here so the reasoning survives, not just the outcome.

| Change | Was | Now | Why |
|---|---|---|---|
| Name for the lab | "Studio" | "Lab", used as a descriptor, never "Fundaments Lab" | The credit line reads "Fundaments.work"; "lab" describes it without becoming part of the name |
| Lab site design | Carbon, lime, Inter, JetBrains Mono | Carbon and lime kept, on the shared system | The palette is the lab's identity; the system is the layer above it |
| System base | Theorem's page covered Theorem only | Theorem's rules become the system | One system, not two dialects |
| Mono typeface | JetBrains Mono and DM Mono | DM Mono everywhere | One data face across the lab |
| Sans typeface | Inter | DM Sans, 300 and 400 | Hierarchy from size and colour, not weight |
| Dark theme | Not defined | Theorem's shipped dark values | The app is what users see |
| State colour | Stone for reading progress only | One accent for the lab, one meaning | Colour alone never carries state |
| Product accents | Theorem Stone, lab lime | Lime everywhere | Two accents were a second dialect |
| Navigation | Collapsible sidebar with labels | Fixed 48px rail, icons only, tooltips, 2px accent edge on the open item | The open item is a signal, not a drawer |
| Icon buttons | Bordered box with hover background | Bare icon, no box and no fill; hover is the accent colour | Depth is by tonal step, not by hover fill |
| Credit line | Set per site, lowercase on Theorem | One spec: Fundaments.work, DM Mono, 0.35 × wordmark | Repeated identically everywhere |
| Clear space | Mark height, or nucleus diameter | One mark height for every mark | One rule, not two |
| Lemma | Inherits Obsidian by accident | Out of scope, inherits Obsidian by decision | It runs inside someone else's app |
| Collaboration terms | Badges only | Allowed, ask first, not permitted | Third parties need to know the boundary |

### Still open

- **Highlight labels.** The colours are fixed; Theorem's runtime labels
  them Important / Key Idea / Interesting / Critical / Action / Beautiful
  while this document says Core thesis / Method / Agreement or fact / Quote
  / Question / Contradiction. One canonical set is needed.
- **Lemma** has no mark on the 24 grid.
- **Licensing.** Whether MIT and CC-BY 4.0 cover the marks is unverified.
  The assumption here is that they do not.

### Sources

- [Fundaments.work brand guidelines](https://fundaments.work/brand/)
- [Theorem brand guidelines](https://theorem.fundaments.work/brand/)
- Theorem's `design-tokens.css` and `design-tokens.ts`, read 2026-10-11

---

## 9 · Adoption

How each product gets onto the system. No build step; this is a read and
an edit.

### Theorem

On the system. Dark is the default, lime is the default accent, the
sidebar is a fixed rail, and weights are 300 and 400. Its `design.md` is a
pointer to this repository. Still open: settle the highlight labels in
`design-tokens.ts`.

### Fundaments.work

Swap Inter and JetBrains Mono for DM Sans and DM Mono, rebalance headings
onto weight 300 and −3% tracking, then drop the two `@fontsource`
dependencies and regenerate `brand/exports`, which are rasterised
in Inter today.

### Lemma

Nothing in the app — it inherits Obsidian. A Lemma landing page uses the
lab's tokens like any other lab page.

### Theorem's copies

`design.md` in `Theorem` and in `theorem-landing` are pointers here. The
`ds-bundle/` UI kit is retired.