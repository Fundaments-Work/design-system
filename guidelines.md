# Fundaments.work Design System — Guidelines

v1.1 · 2026-10-19

One system for the lab and every product it makes. Square, quiet, and set
in two weights. Token values live in [`tokens.md`](./tokens.md); this
document is the language around them.

Sections 1 to 7 are the core language: structure, marks, lockup, colour, type,
rules and collaboration. Sections 8 to 27 apply it to every thing the lab
makes, from marketing sites and desktop apps to terminal output and email, and
end with a checklist for adding a product. Sections 28 and 29 record decisions
and adoption. Where a rule needs a value that did not exist, it is in
`tokens.md` marked **new**.

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
| Manang | Writing papers, theses and slides | Acid lime, sage for math | Dark, with a light theme |
| Lemma | Flashcards, spaced repetition | None in-app — Obsidian owns it | Inherits Obsidian |

The lab site keeps carbon, lime and the system. That question is settled:
the lab's palette is a value set, and the system is the layer above it.

---

## 2 · Marks

Drawn from geometry. Theorem is rectangles on a 24-unit grid. The lab's
mark is an F and a proof square on a 512 grid. Corner radius is 0 for
both, and no mark is typed, rotated, skewed or outlined.

- **Theorem** — bar 16 × 4, stem 4 × 8, foot 4 × 4. The foot is the
  square that closes a proof.
- **Fundaments.work** — an F with no middle arm, stem and cap 48 thick, and
  a lime 48 square where the middle arm would end: the proof is the part the
  letter is missing. Construction hairlines cross at the square's centre.
  512 grid. The official SVG governs; the values here are for reference.

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
| Manang | Acid lime `#c6f135`, sage `#b3d17a` | Lime is the one signal; sage marks math and search matches, sparingly |
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

Measured on the base `#141416`. The full table, with every surface, is in
[`tokens.md`](./tokens.md#surface-and-text-pairings).

| Pair | Ratio | |
|---|---|---|
| Text on base | 14.75:1 | AAA |
| Secondary on base | 7.04:1 | AAA |
| Muted on base | 5.91:1 | AA |
| **Lime on base** | **14.05:1** | AAA |
| Line on base | 1.70:1 | decorative |
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

## 8 · Surfaces

Everything the lab ships is a surface. This section says which tokens each
one takes, so the sections after it only have to say what is particular.

| Surface | Base | Accent | Type | Radius | Section |
|---|---|---|---|---|---|
| Marketing site | dark, shared | lime, one action | DM Sans 300/400, DM Mono | 0 | [16](#16--marketing-sites) |
| Docs site | dark, shared | lime | DM Sans, DM Mono | 0 | [17](#17--docs-sites) |
| Desktop app | dark, shared; light is a theme | lime, one signal | DM Sans, DM Mono | 0 | [18](#18--desktop-apps) |
| Obsidian plugin | **host theme** | host accent | host fonts | host | [19](#19--obsidian-plugins) |
| CLI, installer script | the user's terminal | lime, one thing | the user's terminal | n/a | [20](#20--cli-terminal-output-and-install-scripts) |
| README, repo page | GitHub's | none; the mark and badges | GitHub's | n/a | [21](#21--readmes-badges-and-github-repositories) |
| Release notes | GitHub's, app dialog | none | as above | n/a | [22](#22--release-notes-and-changelogs) |
| App icon, installer | dark field | mark only | n/a | 0 | [23](#23--app-icons-and-installers) |
| Screenshots, demos | the product's own | the product's own | the product's own | 0 | [24](#24--screenshots-and-demo-capture) |
| Social image | dark, shared | lime, one | DM Sans, DM Mono | 0 | [25](#25--social-images) |
| Email | dark where the client allows, with a plain fallback | lime button | system sans fallback | 0 | [26](#26--email) |

### What never changes

On any surface where the lab controls the pixels: radius `0`, 1px hairlines,
no shadows, two weights, one accent with one meaning, depth by tonal step,
state never by colour alone, and the credit line unchanged.

### What gives way

Where a host owns the pixels (Obsidian, a terminal, GitHub, an email client,
an operating system dialog) the host's rules win and the lab's rules shrink to
what the host leaves open: voice, honest claims, and the mark and badges where
the host allows an image. A product that forces the system onto a host is
wrong, not consistent.

---

## 9 · Voice and copywriting

The system is quiet, and the words are too. This applies to every string: UI,
docs, errors, releases, READMEs, email. Example strings in this document show
the form; they are not facts about any product, so check them before reuse.

### Rules

- **Plain sentence case.** Buttons, menus, headings, dialog titles. "Save a
  version", not "Save A Version". Proper names keep their capitals:
  Fundaments.work, Theorem, Lemma, Manang, Typst, LaTeX, Markdown.
- **Say what is true, once.** No superlatives, no "powerful", "seamless",
  "blazing", "revolutionary", "effortless", no "simply" or "just". If a claim
  can be a number or a file name, make it one, in DM Mono.
- **Verbs for actions, nouns for places.** "Export PDF", "Trash".
- **Present tense, active voice.** "Manang saves a safety copy first", not
  "A safety copy will be saved".
- **No exclamation marks.** No emoji in product copy, docs, releases or
  READMEs.
- **No blame.** Never "you entered an invalid…". Name the thing, not the
  person.
- **One idea per sentence.** Dashes are for ranges and for pairs such as
  "Closed — 14 items"; do not chain clauses with them.
- **Claims about privacy are literal.** "No telemetry" is written only where
  the product sends none. It is never softened to "minimal" or "anonymous".
  This is the same test as the Zero Telemetry badge.
- **Numbers.** Digits for every number in UI and docs. Units with a space and
  in mono where they are data: `14 MB`, `220 ms`. Dates are `2026-10-19`.
- **Lists have one grammar.** Every item in a list is a fragment or every item
  is a sentence.

### Error messages

Three parts, in this order, in plain words: **what happened**, **why** if it is
known, **what to do next**. Put the technical detail after, in mono, where it
can be copied.

| Don't | Do |
|---|---|
| Something went wrong. | Manang could not save `thesis.typ`. The disk is full. Free some space and try again. |
| Error: ENOENT | `figures/plot.svg` is missing. It was in the project last time. Restore it from the trash or remove the line that includes it. |
| Invalid input! | The project name cannot contain `/`. |
| Failed to connect to server. | Could not reach `relay.fundaments.work`. Your document is saved on this computer; sharing resumes when you are online. |

Rules: no "Oops", no "Sorry" as a substitute for a next step, no raw error
codes without a sentence before them, and never a dead end: every error names
one action, or says that nothing needs to be done.

### Empty states

An empty state says what belongs here, then offers the one action that fills it.
It does not apologise, joke or decorate.

| Where | Write |
|---|---|
| Empty trash | Nothing in the trash. Deleted projects and files wait here until you empty it. |
| No search results | No matches for `fig`. Check the spelling or search all files. |
| No projects | No projects yet. Open a folder or start from a template. |

An empty state has no illustration, at most one mark-sized glyph from the icon
set, and exactly one primary action.

### Confirmations and destructive actions

Name the object and the consequence, and label the button with the verb:
"Delete project" and "Keep project", never "OK" and "Cancel". If the action
can be undone or restored, say where. Destructive buttons use the text colour
on a hairline, with `--danger` only for the word "Delete" in the title when the
action cannot be undone.

### Words for things

| Use | Write | Never write |
|---|---|---|
| Local storage | on your computer, on your device | in the cloud (unless it is) |
| Cost | free, open source, MIT | freemium, for now |
| What we are | an independent lab | company, startup, agency |
| Beta status | public beta, with the licence and the download place | stealth, early access |
| The user | you | the user, users, folks |

---

## 10 · Accessibility

The floor, not the goal. Targets WCAG 2.2 AA everywhere, and AAA for body text
on the base where the tokens already give it.

### Contrast, measured

| Need | Minimum | Tokens that meet it on the base |
|---|---|---|
| Body and UI text | 4.5:1 | Text 14.75, Secondary 7.04, Muted 5.91, Lime 14.05, Sage 10.79 |
| Large text (24px, or 19px at 400) | 3:1 | everything above |
| Control boundary, focus ring, icon that carries meaning | 3:1 | Border strong 3.42, Lime 14.05 |
| Decorative hairline | none | Line 1.70, never the only cue |

The full pairing table is in [`tokens.md`](./tokens.md#surface-and-text-pairings).
Numbers are computed from the values, not eyeballed. Recompute when a token
changes; a pair that nobody measured is a pair that fails.

### Rules that follow from the numbers

- Secondary and muted text on the **hover** surface fail (3.65:1 and 3.07:1).
  On a hovered or selected row, text steps up to the primary colour.
- A bordered control on the **raised** surface cannot use Border strong
  (2.73:1). Use a tonal step and no border, or a lighter boundary that clears
  3:1.
- Disabled text is for disabled things only (4.29:1 on the base). It never
  carries information a reader needs.
- Lime is never body text on a light surface (1.24:1). The light accent is
  olive `#4d6a00`, 5.91:1 on paper.
- Text over an image or a gradient does not exist in this system, so there is
  nothing to calculate. Do not add it.

### Keyboard

- Every action reachable by pointer is reachable by keyboard, in reading order.
- Tab order follows the visual order. Do not set `tabindex` above 0.
- Menus open with `Enter` or `Space`, move with arrow keys, close with `Esc`,
  and return focus to what opened them. Desktop apps add `Alt+letter`
  mnemonics and `F10` for the menu bar, as Manang does.
- Dialogs trap focus, label themselves with their title, close on `Esc`, and
  put initial focus on the least destructive control.
- Every shortcut is listed in the product, in DM Mono, and can be rebound
  where the product has keybindings.
- A skip link is the first focusable element on every web page.

### Focus

- Ring: `2px solid var(--accent)`, no radius. Offset `3px` on the web. In a
  dense desktop row, use `outline-offset: -2px` so the panel does not clip it.
- Never remove an outline without drawing another. `:focus-visible`, not
  `:focus`, so a mouse click does not show the ring.
- The focus ring is the same lime signal as the open item. It does not count
  as a second signal in the frame.
- Inputs may also move their border to lime on focus, as the site's fields do,
  as long as the ring is not removed.

### Colour is never the only cue

State is colour **and** a label or a shape: an icon, a word, a position, an
underline. Errors carry `--danger` and an icon and the text "Error" or the
problem itself. Git status in a file tree is a letter (M, A, D, U), not just a
colour.

### Other

- Text resizes to 200% without loss. Use `rem` or `em` for text; pixels for
  borders and hit targets.
- Hit targets are 24 × 24px with a pointer and 44 × 44px for touch.
- Every image that carries meaning has alt text that says what it shows;
  decorative images have `alt=""`. Charts follow [section 14](#14--data-visualisation-charts-and-diagrams).
- Do not rely on hover for anything. Tooltips repeat a label that is also
  available on focus.
- Respect `prefers-reduced-motion` ([section 12](#12--motion)).
- Set `lang` on the document. Set `color-scheme` to what the page is: `dark`
  for a dark-only page, never the default.

---

## 11 · Iconography

One icon family, drawn from the same shapes as the marks.

- **Grid and stroke.** 16-unit grid, 1.25 stroke, butt caps, mitred joins.
- **Shapes.** Squares, rules and diagonals. No circles, no rounded caps, no
  rounded joins. A round thing (a clock, a dial) is drawn as a square with a
  rule.
- **Fill.** None. Icons are outlines in `currentColor`.
- **Sizes.** 16px in controls, 20px in navigation, 24px on marketing pages. Not
  scaled to other sizes.
- **Colour.** `currentColor`. The default is the secondary text colour; hover
  and the open item use the accent. An icon never has its own hue.
- **Buttons.** An icon button is a bare icon: no box, no fill, no hover
  background. Hover is the accent. Its target is 24px with a pointer and 44px
  for touch.
- **Labels.** An icon that stands alone has an accessible name and a tooltip
  with the same words, and the tooltip also shows on keyboard focus.
- **No icon packs.** Do not pull in a general-purpose icon library that
  brings circles and 24-grid curves. Draw the icon in the family, or use a
  word.
- **Emoji are not icons.** Do not use them in a product, a README or release
  notes.
- **The mark is not an icon.** Do not use the lab's F or the turnstile as a
  bullet, a loading spinner or a decoration.

---

## 12 · Motion

Motion confirms that state changed. It never decorates.

### Allowed

| Motion | Duration | Curve |
|---|---|---|
| Colour, border, opacity change (hover, focus, toggle) | 150ms | `cubic-bezier(0.22, 1, 0.36, 1)` |
| Panel, menu, dialog enters or leaves | 220ms | same |
| Layout move, large reveal, page transition | 320ms | same |

Properties that move: `opacity`, `transform` (translate only, up to 12px), and
`color`/`background-color`/`border-color`. Nothing that animates layout
properties (`width`, `height`, `top`) on a path a user triggers repeatedly.

### Not allowed

- Bounce, spring, elastic, overshoot, or any curve other than the standard one.
- Parallax, auto-playing video, looping decorative animation, spinners that are
  not tied to real progress.
- Motion longer than 320ms. If it needs more, it is doing too much.
- Blur, glow and scale-up "pop" effects.
- Moving text while someone is trying to read it.

### Loading and progress

A wait under 300ms shows nothing. A longer wait shows a progress bar (a 2px
accent rule) when progress is known, and a mono label otherwise: "Compiling…".
No spinners that rotate, because a rotation is a circle.

### Reduced motion

Under `prefers-reduced-motion: reduce`, every transition and animation drops to
`1ms` (the site's rule), nothing slides, and scroll-linked effects are
replaced by the end state. Information that was carried by motion (a new item
appearing) must also be carried by a label or a position change. Test with the
setting on; "it still works" is the bar.

---

## 13 · Interface patterns

### Tables

- Hairline grid, `1px #3d3d42`, no zebra stripes, no filled header.
- Header row: DM Sans 400 in secondary text, sentence case, not bold. A number
  column is right-aligned and set in DM Mono; a text column is left-aligned.
- Cell padding `8px 12px` (the docs value). Dense desktop tables use `4px 8px`
  with a 24px row.
- Row hover uses the hover surface with primary text; the selected row adds a
  2px accent edge on the leading side, which is the one signal.
- Long tables scroll inside their own container at phone width; the page does
  not scroll sideways. Keep the first column visible.
- Sort state is an arrow icon and `aria-sort`, not colour.
- Every table has a caption or a heading directly above it.

### Forms

- Label above the field, DM Sans 400, 13px, always visible. A placeholder is an
  example, never a label.
- Field: recessed background `#0d0f0a`, `1px` boundary in Border strong
  (3.42:1 on the base), 40px high on the web, 28px in a dense desktop panel.
  Text 13px (desktop) or 15px (web). On focus the border turns to lime and the
  ring stays.
- Help text sits below the field in secondary text, 12px. Say what the field is
  for and any constraint before the person types, not after they fail.
- Required fields are marked with the word "Required" in mono, not an asterisk
  alone. Prefer optional marking only when most fields are required.
- One primary button per form, aligned to the end; the secondary is a
  hairline button. Disable nothing silently: if a button cannot be pressed, say
  why next to it.
- Checkboxes, radios and switches are squares and rectangles. A checked state is
  a mark inside plus the label; a switch is a rectangle with a square knob, and
  shows "On" or "Off".
- Use real inputs, labels and `fieldset` / `legend` so assistive technology
  works.

### Validation messages

- Validate on blur or on submit, not on every keystroke, unless it is a live
  constraint such as a name that is already taken.
- The message sits directly under the field, in `--danger`, with a 16px error
  icon and the words, linked with `aria-describedby`. The field's border turns
  to `--danger`.
- On submit with errors, move focus to the first invalid field and show a
  summary at the top: "2 problems to fix" with links to each field.
- Say how to fix it, not that it is wrong: "Use 3 to 64 characters", not
  "Invalid name".
- A success message is plain text with a check and a label ("Saved"), in the
  text colour, for 4 seconds, in a live region. No green.

### Error states

- Inline error: an error icon, a sentence per [section 9](#9--voice-and-copywriting),
  `--danger` for the icon and the first line only.
- Blocking error: a dialog with the title naming what failed, the body saying
  why and what to do, one primary action, and a "Copy details" button that
  copies the technical text in mono.
- Page-level error (404, offline, failed load): the mark at 56px is allowed, a
  one-line headline, one sentence, one link home. No jokes, no illustration.
- An error never replaces content that was already usable. Keep what loaded and
  say what did not.

### Empty, loading and partial states

- **Empty**: wording in [section 9](#9--voice-and-copywriting).
- **Loading**: skeletons are hairline boxes in the raised surface, with no
  shimmer. A mono label names what is loading.
- **Partial**: show what exists with a line naming what is missing and how
  many: "Showing 12 of 40. 28 could not be read."

### Dialogs, menus and tooltips

- A dialog sits on the surface tone with a `1px` hairline, no shadow, over a
  scrim of `rgb(0 0 0 / 0.78)`. No blur. Corners are square. One dialog open at a
  time.
- Menus are the surface tone with hairline dividers between groups, 28px rows,
  the shortcut right-aligned in mono. The focused row uses the hover surface.
- A tooltip is mono 11px on the raised surface with a hairline, appears after
  500ms on hover or immediately on keyboard focus, and never holds anything the
  control does not already say.

---

## 14 · Data visualisation, charts and diagrams

Draw the data, not decoration. The palette is ink, one signal and a ladder of
neutrals.

### Colour

- Use the slots in [`tokens.md`](./tokens.md#chart-colours). `--chart-focus`
  (lime) is the one series or point the chart is about. It is the one signal
  for the frame.
- A chart with no focus uses text and neutrals only.
- Up to five series. Beyond five, use small multiples (the same small chart
  repeated), not a sixth colour.
- The six highlight colours are for Theorem's highlights. They never colour
  chart series.
- Do not use `--danger` for "bad" data. If a value is a failure, label it.
- Sequential data uses the accent mixed into the surface in five steps
  (20, 40, 60, 80, 100%). There is no diverging palette; use a centre line and
  two labels.
- Canvas-based chart libraries cannot resolve `var(--x)`. Read the computed
  value with `getComputedStyle` and pass the hex. This is a known drift in
  Lemma.

### Marks and layout

- Bars and areas have square ends. Lines are `2px`, with square joins and butt
  caps. Points are squares, 6px. No circles, no rounded bars, no gradients, no
  3D, no pie or donut charts.
- Gridlines are `1px` `--chart-grid`, horizontal only unless the chart needs
  both. No chart border. Baseline is `--text-60`.
- Axis labels and values are DM Mono 11px in `--chart-axis`. Titles are DM Sans
  300 in text colour, above the chart, left-aligned.
- Label lines and bars directly at their end, and keep the legend for
  six-plus items. Direct labels beat a legend.
- Distinguish series by more than colour: direct label, dash pattern
  (`6 4` for the second series) or marker position.
- Start bar axes at zero. A line chart may start elsewhere only if the axis says
  so.
- Always show units and the date range. Mono for numbers; thousands separated by
  a thin space, not a comma, in tables.

### Accessibility and export

- Every chart has a text summary above it or a table below it with the same
  numbers. The table is the accessible version.
- A chart's alt text states the finding ("Compile time fell from 4.1 s to 1.9 s
  between v0.1 and v0.4"), not "Line chart".
- Charts in READMEs, release notes and social images are SVG on the base `#141416`
  background, or PNG at 2× with the same background.

### Diagrams

- Boxes are squares with a `1px` line in `--text-60`; the focus box is the only
  one with a lime edge. Arrows are straight or right-angled lines with a
  square arrowhead.
- Text in diagrams is DM Sans 12px or DM Mono 11px, never below 11px, in text
  colour.
- Flow runs left to right or top to bottom; do not mix.
- Diagram tools that generate their own style (Mermaid and similar) are
  configured with these tokens: base background, `#3d3d42` lines, text colour
  `#e8e6e1`, no rounded nodes, DM Sans. If a tool cannot be made to comply, do
  not publish its default look.

---

## 15 · Code blocks and syntax colour

- **Surface.** Recessed `#0d0f0a`, `1px` hairline, square, no shadow. Padding
  `12px 16px`. A code block does not float on a lighter panel.
- **Face.** DM Mono 400, 13px in docs and READMEs (12px in dense desktop
  panels), line height 1.5. Inline code is mono at 0.9em on recessed with a
  hairline, as the docs site draws it.
- **Colour.** The roles in [`tokens.md`](./tokens.md#syntax-colour): text,
  secondary text for strings and punctuation, muted italics for comments, sage
  for names and labels, lime for links only. Never a full rainbow theme, never
  a theme that paints keywords lime, because lime is the one signal in the frame.
- **Weight.** Regular only. Keywords are not bold.
- **Wrapping.** Scroll horizontally inside the block. Do not wrap a command
  that someone will paste.
- **Titles and prompts.** A block that shows a terminal command has no prompt
  character in the copyable text. If a `$` is shown, it is outside the copy
  target.
- **Diffs.** `+` and `-` lines are marked by the characters in the margin and a
  tonal wash (accent at 20% for added, `--danger` at 20% for removed), never
  colour alone, never solid fills.
- **Copy button.** An icon button at the top end, with the label "Copy" on focus
  and "Copied" for 2 seconds.
- **Long output.** Collapse beyond 40 lines with "Show all 120 lines".
- **Tool defaults.** Highlighters that ship a theme (Shiki, Expressive Code,
  Prism) are set to this palette; a stock theme is a defect. The docs site
  already draws the surface and border; the token colours are the remaining
  work and are tracked under Known drift.

---

## 16 · Marketing sites

The lab site (`fundaments-landing`) and a product's landing page (`theorem-landing`) are the references.

### Structure

- Dark only. Set `color-scheme: dark` and `<meta name="color-scheme" content="dark">`
  and `theme-color` to the base `#141416`. Do not ship a theme switch that cannot
  be honoured: lime is 1.24:1 on paper.
- Content is in a `.wrap`: max width 1360px, gutter 20px (40px from 768px up).
- Sections are separated by a `1px` hairline and `96px` of vertical padding.
  Do not alternate section backgrounds. Panels use the surface tone; inset areas
  use recessed.
- One headline per page, in Display or Headline, Sans 300 at −3%. The first
  view holds the headline, one sentence of at most 34em, and one primary
  action.
- One primary action per view. It is the lime button: 48px high, DM Sans 300 at
  15px, 22px side padding, square. The secondary action is the hairline button.
  A third action is a text link.
- Links in text are underlined; the underline grows from 0 to 100% on hover.
  Navigation links are secondary text and turn to the accent on hover.
- Copy comes from data files, not from templates, so one source of truth and one
  voice.

### Layout and imagery

- No photography, stock imagery, gradients, glassmorphism, shadows or
  decorative illustration. Imagery is a real screenshot ([section 24](#24--screenshots-and-demo-capture)),
  a mark, or a diagram.
- Cards and tiles are rectangles with a hairline. There is no card shadow and no
  hover lift. Hover changes the border or the title to the accent.
- Grids are 12 columns at desktop, 1 at phone. Gaps from the spacing scale.
- Numbers that matter ("0 bytes of telemetry") are set large in Display and
  accompanied by a mono caption of what they measure.

### Metadata

- Page title is `<Page> — Fundaments.work`; the home title is the one sentence
  of what the lab is. Descriptions are one plain sentence, under 160
  characters.
- Open Graph and Twitter cards: `og-fundaments-1200x630.png` for the lab, the
  product's own card for a product. Both `summary_large_image`.
- Favicon is the mark SVG. Every static asset served for brand use stays at
  `/brand/<file>`.
- No cookies banner is needed because there are no cookies. If one ever becomes
  needed, the principle has failed; do not design a banner for it.
- No analytics script, no third-party font host, no embed that phones home.
  Fonts are self-hosted from `/fonts/`.

### Performance

- Preload the one display font. Subset to Latin. Serve fonts and brand files
  with `Cache-Control: public, max-age=31536000, immutable`.
- Target LCP under 2.5s on a mid phone. No layout shift: reserve image and font
  space.
- Motion per [section 12](#12--motion); Lenis-style smooth scroll or GSAP
  reveals must be disabled under `prefers-reduced-motion`.

---

## 17 · Docs sites

Documentation is a reference surface, not a product. It follows the system
as a theme on the docs framework, and it keeps the framework's behaviour.

### Starlight theming rules

The lab's docs site runs Starlight. These are the rules the theme file
follows, and the ones a new docs site copies.

1. **Every colour resolves through tokens.** Map the framework's variables
   (`--sl-color-*`) onto the system tokens in one stylesheet and invent
   nothing: background `#141416`, nav and sidebar the same, hairline `#3d3d42`,
   text `#e8e6e1`, accent lime, accent-low recessed, inline code recessed.
2. **Dark only.** Replace the theme select and theme provider with empty
   components. Leaving the provider in writes a `data-theme` attribute that
   re-enables the framework's light variables.
3. **Radius `0`, with a backstop.** The framework writes literal radii into its
   component styles. An unlayered `* { border-radius: 0 !important }` in the
   theme stylesheet beats them; the stylesheet must not be wrapped in a layer.
4. **Two weights, with a backstop.** Reset `font-weight` to 400 and headings
   to 300. Never let the framework's 600 and 700 request a synthesised bold.
5. **No shadows.** Set `--sl-shadow-sm`, `-md` and `-lg` to `none`.
6. **Callouts without hues.** Map the framework's blue, purple, orange, red and
   green onto accent or neutrals, and label every callout with its type word
   ("Note", "Caution", "Danger"). The label carries the meaning.
7. **Fonts.** Self-host DM Sans 300, 400 and DM Mono 300, 400 under `/fonts/`;
   map `--sl-font` and `--sl-font-mono`. Do not load a font host.
8. **Line height 1.6**, not the framework's 1.75; measure about 65 characters.
9. **Tables** are hairline grids without zebra fill; **code** sits on the
   recessed surface with a hairline ([section 15](#15--code-blocks-and-syntax-colour)).
10. **The title links to the docs home**, not the marketing site; the marketing
    site's header links to the docs.
11. **No "Edit this page" on pages written in the site's repo**; synced pages
    link to the repo they came from.

### Structure

- The sidebar groups **products** first, one group per product, each with an
  overview, a guide, and where it applies a changelog and known issues.
  Reference material that is not a product sits in its own group after them.
- **The design system is a reference, not a product.** It has no logo, no
  version badge and no "Get it" button, and it sits in the Reference group.
- Page titles are sentence case. The first sentence says what the page is for.
- A page is one topic. Over about 800 lines or when a reader would need a table
  of contents to find a rule, split it; otherwise add anchors.
- Every procedure is numbered and each step starts with a verb. Commands are in
  code blocks; the expected output follows in a second block.
- Link text names the destination ("the install guide"), never "here".
- Search is local (Pagefind). No third-party search service.
- Pages generated from another repo carry a marker comment and are never edited
  by hand; the sync reports any link it had to turn into text.

### Writing

- Sentence case, second person, present tense, per [section 9](#9--voice-and-copywriting).
- State the version a page is about when it matters, in mono: `v0.4`.
- Screenshots follow [section 24](#24--screenshots-and-demo-capture). A page
  never depends on a screenshot to be understood.
- Known limitations are listed plainly on the page they affect, not hidden in
  an issue tracker.

---

## 18 · Desktop apps

For Tauri and Svelte apps (Manang is the reference; Theorem follows the same
rules). The shell is thin: it renders and dispatches.

### Window and chrome

- **Dark only by default**, `theme: "Dark"` in the window config, with the
  light theme available as a setting. The native frame is off
  (`decorations: false`) and the app draws a 40px top bar: mark, product name,
  context, command search, window controls. The drag region is the bar, minus
  its controls.
- Default window 1280 × 820, minimum 640 × 480, resizable, centred. Remember
  size and position.
- Window controls are square icon buttons at the platform's end (right on Windows
  and Linux, left on macOS). Close is not red; `--danger` is for errors.
- The app is usable at 640px: the side panel overlays the editor under 800px and
  the top bar folds.

### Layout

- Structure: activity bar (48px, icons, tooltips, a 2px accent edge on the open
  item), side panel (200–480px, default 264px, draggable, double-click to reset),
  tab strip (36px, a 2px accent rule on top of the active tab), editor, bottom
  panel (96–560px), status bar (24px).
- Surface tones step: base for the editor; surface for the panel, tab strip and
  status bar; raised for hover and selected rows; recessed for inputs and code.
  The step is the border; add a hairline only where two same-tone areas meet.
- Dividers are `1px`. Draggable splitters are a `1px` line with a 6px hit area.
- No shadows, no blur, no translucency on chrome. Menus, popovers and dialogs sit
  on a surface tone with a hairline.

### Density and type

- UI text 12px, forms and editor 13px, dialog titles 15px, meta 11px in mono.
  Row height 24px for lists and trees, 28px for menus, 40px for primary rows.
- Spacing from the scale; panel padding 12px, section gaps 16px or 24px.
- Weights 300 and 400. Selection is shown by the hover surface and the accent
  edge, not by weight.
- Content a person reads in the app (a document, an article) may use the
  reading face the product chose, which is content and not interface (Theorem's
  reader keeps its serif).

### Panels, menus, dialogs

- A panel has a header row with a mono title, actions as bare icons at the end,
  and a `1px` bottom hairline.
- The application menu bar is real: File, Edit, View, Go, Build, Help, with
  `Alt+letter` mnemonics and `F10`, and shortcuts right-aligned in mono. On
  macOS use the system menu bar.
- A command palette opens on `Ctrl+K` (`Cmd+K`) and lists every command with its
  shortcut.
- Dialogs: centred, 360–560px wide, title 15px, one primary button, hairline
  secondary, `Esc` closes, initial focus on the least destructive control. The
  content behind sits under `rgb(0 0 0 / 0.78)` without blur. A dialog is never
  used for a message that fits in the status bar or a toast.
- Toasts: bottom-end, 320px, on the raised surface with a hairline, in the
  status bar's voice, auto-dismissed after 6s unless they hold an action, and
  also in a live region. At most one at a time.

### Focus and input

- Focus ring is lime `2px`, offset `-2px` in dense rows. Tab order follows the
  layout: top bar, activity bar, side panel, editor, bottom panel, status bar.
- Text selection inside the shell is off (`user-select: none`) except in fields
  and content; the shell must not select like a web page. Content areas select.
- No rubber-banding: `overscroll-behavior: none`.
- Every command has a keyboard route, shown in the menus and the palette.
- Drag and drop has a keyboard equivalent.

### State, loading and safety

- Unsaved: a square on the tab or row. Modified in version control: a letter.
  Error: the `--danger` icon plus the Problems count in the status bar.
- Destructive actions are recoverable where they can be (trash, version
  history, safety copies) and the dialog says where.
- Long work reports progress in the status bar and can be cancelled.
- Offline is the default. A network feature says what it will contact and asks
  first, and the app works without it.

### Packaging notes

- Self-host fonts. A local-first app never reaches a font host.
- A strict Content Security Policy: `default-src 'self'`, no remote scripts.
- The bundle identifier is `work.fundaments.<product>`, as Manang's is.

---

## 19 · Obsidian plugins

Lemma is the reference. An Obsidian plugin is a guest in someone else's
interface, so the system recedes to what the host leaves open.

### What the plugin UI takes from the host

Everything visual. Use Obsidian's CSS variables and its components; never a lab
hex, never a lab font.

| Need | Use |
|---|---|
| Backgrounds | `--background-primary`, `--background-secondary`, `--background-modifier-hover` |
| Text | `--text-normal`, `--text-muted`, `--text-faint`, `--text-error` |
| Accent and links | `--interactive-accent`, `--text-accent` |
| Borders | `--background-modifier-border` |
| Fonts | `--font-interface`, `--font-text`, `--font-monospace` |
| Radius and spacing | Obsidian's own (`--radius-s`, `--size-4-*`) |
| Icons | Obsidian's `setIcon` set, not the lab's |
| Controls | `Setting`, `Modal`, `ItemView`, `ButtonComponent` |

### Tokens that do **not** apply in the plugin

Radius `0`, the lab base and lime, DM Sans and DM Mono, 1px hairlines at
`#3d3d42`, and the no-shadow rule. A square, lime plugin inside a rounded theme
is the bug, in every theme.

### What still applies

- **Voice** ([section 9](#9--voice-and-copywriting)) in every string: sentence
  case, errors that say what to do, empty states that offer one action.
  Obsidian also asks for sentence case.
- **Accessibility** ([section 10](#10--accessibility)): keyboard reachable,
  labelled controls, text that follows the theme's contrast. Test in the
  default dark and light themes and one community theme.
- **Motion**: honour reduced motion; 150–220ms or none.
- **Meaning is not colour alone.** Ratings, due dates and statuses carry a
  label. Where the plugin needs state colour beyond Obsidian's, derive it from
  `--interactive-accent` and `--text-error` rather than hard-coding hues.
- **Canvas and charts**: resolve variables with `getComputedStyle` before
  handing a colour to a canvas library; re-read on `css-change`.
- **Shadows**: a plugin does not add its own. Hard-coded hex shadows that
  fight a theme are the defect Lemma's drift row records.
- **No telemetry**, and say so only if true.

### Published surfaces

The plugin's README, listing text, screenshots, release notes and badges follow
the lab's rules: the mark and badges in the README, the voice, the release-notes
format. The Obsidian badge names a third party, so follow Obsidian's own terms.
The plugin name is "Lemma" and never "Obsidian Lemma"; say "a plugin for
Obsidian".

---

## 20 · CLI, terminal output and install scripts

The terminal belongs to the user. The lab controls words and, lightly, one
colour.

### Output

- **Plain text first.** The output reads correctly with no colour and no
  Unicode beyond Latin and `—`.
- **Colour only on a TTY.** Write colour when stdout is a terminal, `NO_COLOR`
  is unset and `TERM` is not `dumb`. Honour `--no-color`. Write 24-bit colour
  only when `COLORTERM` is `truecolor` or `24bit`, otherwise the 16-colour
  fallback from [`tokens.md`](./tokens.md#terminal-output).
- **One accent per screen**, on the thing that matters: the final line saying
  it worked, or the one value to act on. Errors use the red fallback. Never a
  background colour, never blinking, never a rainbow.
- **No emoji, no box-drawing art, no banner.** The credit line, if printed at
  all, is the last line: `Made by Fundaments.work`.
- **Progress.** On a TTY, one line rewritten with `\r`, showing what is
  happening and a count: `Downloading v0.1.0-beta.2 (41 of 96 MB)`. Not a TTY:
  one line per step, no rewriting.
- **Streams.** Results to stdout, logs and errors to stderr. Exit `0` on
  success, non-zero on failure, and a distinct code for "nothing to do" only if
  documented.
- **Width.** Do not assume more than 80 columns; wrap prose at 72.

### Messages

- Errors follow [section 9](#9--voice-and-copywriting): `error: <what happened>.
  <what to do>.` in lower case after the `error:` prefix, one line where
  possible, as the Manang install script does.
- Prefix status words, not decoration: `error:`, `warning:`, `note:`.
- Every message that mentions a file or URL prints it whole, unbroken, so it
  can be copied.

### Flags

- `--help` and `-h` print usage, flags with one-line descriptions, and a
  pointer to the docs. `--version` prints the version only.
- Long flags in lower-case kebab: `--dry-run`, `--print-latest`, `--user`.
  `--dry-run` shows what would change and changes nothing. Destructive
  operations offer `--yes` for scripts and prompt otherwise.
- Prompts are one line, with the default in capitals: `Remove Manang? [y/N]`.

### Install scripts

The shape of `install-linux.sh` in Manang is the reference.

- `#!/usr/bin/env bash` with `set -Eeuo pipefail`, a comment header with the
  one-line install command and what the script does, and the tools it needs.
- Verify what you download: fetch the checksum file from the same release and
  compare before installing. Refuse on a mismatch.
- Say what will happen before doing it, support `--dry-run`, and install to a
  user directory when `--user` is given so no root is needed.
- Print each step in one line, then a final line with what was installed and
  where, and the exact command to remove it. Ship the uninstall script
  alongside.
- No telemetry, no `curl | sudo bash`, no changing shell profiles without
  asking.
- Name the platform and architecture it supports, and fail with that sentence
  if run elsewhere.
- Pin the install command in docs to a release tag or the `main` script the
  repository owns, and show a checksum-verified alternative for people who do
  not pipe scripts.

---

## 21 · READMEs, badges and GitHub repositories

A repository page is the first surface most people see. GitHub owns the chrome;
the lab owns the first screen of content.

### README structure

1. Product name as the title and one sentence of what it is, in plain words.
2. A line of links: install, docs, changelog.
3. One screenshot of the real product ([section 24](#24--screenshots-and-demo-capture)).
4. A status line that is true: "Public beta", where installers are, and the
   licence. A box quote is fine for status.
5. Why it exists: three to five bullets of what it does, each starting with a
   bold noun phrase and ending in a concrete fact.
6. Install: the command or the download link, copyable.
7. Build from source, contributing, licence, credit.

Rules: no emoji, no more than three badges, no animated banner, no table of
contents unless the README passes 300 lines. A claim in the README is a claim in
the product; do not write "private" or "offline" for something that is not.

### Badges

- Use only the lab's own SVG badges (`fundaments-badge.svg`, `telemetry-badge.svg`,
  `theorem-badge.svg`, `sync-badge.svg`) and tool-neutral status ones (licence,
  release). Never recolour them.
- Height 28px for the lab's badges. They sit in one line directly under the title
  or the links row, not scattered.
- Zero Telemetry only on a project that sends none.
- Alt text states the claim: "Built with Fundaments.work".

### Repository page

| Setting | Rule |
|---|---|
| Name | Product name as written; lower-case kebab for non-product repos (`design-system`, `fundaments-landing`) |
| Description | One sentence under 100 characters, sentence case, no full stop needed, no emoji |
| Website | The product's docs or site, never a placeholder |
| Topics | Lower-case, hyphenated: the category (`latex`, `typst`, `ebook-reader`), the platform (`tauri`, `obsidian-plugin`), and `local-first` or `open-source` where true. Up to 12 |
| Social preview | 1280 × 640 PNG, under 1 MB, on the base `#141416`: mark, product name in DM Sans 300, one line of what it is in DM Mono. Not yet exported; see Known drift |
| Default branch | `main`, protected |
| Features | Issues on, Discussions only if someone reads them, Wiki off (docs live in the repo) |

### Issue and pull request templates

- Issue forms (`.github/ISSUE_TEMPLATE/*.yml`), with `blank_issues_enabled:
  false` and `contact_links` to the docs, known issues and a **private**
  security advisory link.
- Bug form: what happened, what was expected, steps to reproduce, product
  version (mono), operating system, logs. It says what the product does not
  collect, and tells people never to paste keys or private data. Titles
  prefixed `[Bug]: `, with the labels `bug` and a status label where the repo
  uses one.
- Feature form: the problem first, then the proposal, then alternatives. A
  feature request is not accepted without the problem.
- Pull request template: what changed and why, how it was tested, screenshots
  for UI work taken per [section 24](#24--screenshots-and-demo-capture), and a
  checklist whose items can be checked mechanically.
- Labels are lower-case words; colours are the neutral greys and one lime
  label at most, for "good first issue".
- `SECURITY.md` gives a private reporting route. `CODE_OF_CONDUCT.md` and
  `CONTRIBUTING.md` are short.

### Licences

The site footer states MIT and CC-BY 4.0. Whether either covers the marks is
unverified, and the working assumption is that it does not; see
[Collaboration](#7--collaboration) and the open question under Decisions.

---

## 22 · Release notes and changelogs

### Changelog

- `CHANGELOG.md`, Keep a Changelog 1.1 format with Semantic Versioning, newest
  first, with an `[Unreleased]` section on top.
- Headings: Added, Changed, Deprecated, Removed, Fixed, Security. Do not invent
  other headings.
- One bullet per change, starting with a bold noun phrase for the area, then the
  change in plain words and what the reader can now do: "**Trash:** deleted
  projects can be restored from the Trash."
- Dates are `YYYY-MM-DD` in the version heading. Versions are `0.1.0-beta.2`.
- Past tense for Fixed ("Fixed a crash when…"), present tense otherwise.
- Link the issue or pull request in the form `(#123)` at the end where there is
  one.
- Do not describe internal refactors unless they change behaviour or
  performance. Do not list dependency bumps.

### GitHub releases

- Title is the tag: `v0.1.0-beta.2`. Mark betas as pre-releases.
- Body: one paragraph saying what the release is for, then the changelog section
  for the version, then **Install** with the files and the checksum line.
- State what the installers are and are not: "not code-signed yet" if true, with
  what the operating system will say and a link to the install guide.
- Attach checksums (`SHA256SUMS.txt`). Name assets
  `<product>-<version>-<os>-<arch>.<ext>`.
- No marketing, no emoji, no "we're excited". The notes are for the person
  deciding whether to update.

### In-app notes

- A "What's new" dialog shows the changelog section for the installed version
  in the same words. It is never a modal on first launch after an update; it
  opens from Help.
- Update prompts say the version, the size, and what changed in one line, with
  "Update now" and "Later".

### Voice

Say what changed for the reader. Do not say "improved" without a number or a
behaviour. "Compile time for a 200-page thesis fell from 4.1 s to 1.9 s" is a
release note; "Faster compiles" is a slogan. *(Numbers here are examples of the
form; never copy them.)*

---

## 23 · App icons and installers

### The icon

- **Master**: a 1024 × 1024 square SVG on the base `#141416`. No rounded corners
  and no gradient, shadow, glow or bevel. The product mark is centred in
  `#e8e6e1`; the lab's F is `#e8e6e1` with its square in lime.
- **Safe area**: the mark's bounding box is centred and measures 50% of the
  width for a new product. Theorem's turnstile is drawn at 33.3% and the lab's
  F at 56.25% of the height; both stay as drawn. Nothing else sits in the icon.
- **Never** put the wordmark, the credit line or a badge in an app icon.
- **One mark, every size.** Do not draw a simpler mark for small sizes. Below
  16px the mark is not used; the favicon is the smallest mark. The lab's
  construction hairlines are not part of the mark: they are drawn at 64px and
  above and left out below, with nothing else changed.
- **Platform masks.** iOS and Android apply their own masks. Supply a full-bleed
  square and let the platform cut it. The corners the user sees are the
  platform's, not ours.
- **Android adaptive icons**: foreground on a 108dp layer with the mark box at
  most 43% of the layer, background the base colour on a separate layer.
- **macOS** icons are a full-bleed square from the same master; whether the
  system's template shape needs baking in is an open question under Decisions.
- **Monochrome variant** (Android themed icons, tray icons): the mark in a
  single colour on transparent, 1:1, drawn from the same SVG.

### Sizes to produce

Generate every raster from the master SVG; never edit a PNG.

| Target | Files |
|---|---|
| Source | `icon.svg` (1024), `icon.png` (1024) |
| Tauri | `32x32.png`, `128x128.png`, `128x128@2x.png` (256), `icon.icns`, `icon.ico`, written by `tauri icon` from the master |
| Windows Store tiles | `Square30x30Logo.png`, `Square44x44Logo.png`, `Square71x71Logo.png`, `Square89x89Logo.png`, `Square107x107Logo.png`, `Square142x142Logo.png`, `Square150x150Logo.png`, `Square284x284Logo.png`, `Square310x310Logo.png`, `StoreLogo.png` |
| Linux | `128x128.png` in the hicolor theme; an SVG where the format is accepted |
| Web | `favicon.svg`; an `apple-touch-icon` at 180 × 180 if the page is installed |

Use the Tauri CLI's icon generator on the master, and check each size by eye at
actual size: the mark must be legible at 32px.

### Installers

- Names: `<Product>_<version>_<arch>.<ext>` or the packager's convention, always
  with the version and architecture, and attached to a GitHub release with a
  `SHA256SUMS.txt`.
- Metadata: product name written correctly, one-line description in sentence
  case, publisher "Fundaments.work", the licence, the homepage.
- Installer images (Windows wizard banner and sidebar, DMG background) are the
  base colour with the mark and no other art. The DMG window shows the app and
  an Applications link on the base colour. Keep any text in DM Sans and DM Mono.
- No bundled offers, no telemetry opt-out screen, no first-run survey.
- Say plainly if an installer is not code-signed, in the release notes and the
  install guide, and what the operating system will show.
- Packaging manifests (Homebrew, winget, AUR) carry the same one-line
  description and licence, and point at the release assets.

---

## 24 · Screenshots and demo capture

A screenshot is a claim about the product. It has to be true, current and
legible.

- **Real product, real build.** Capture the desktop app, not a mock. If a
  screenshot comes from a browser build with sample data, say so in the
  caption, as Manang's README does.
- **Size.** 1440 px wide at 2× (2880 px), PNG, for the full window. A phone
  capture is 375 px wide at 3×. Crop to the window, not the desktop.
- **State.** Dark theme (the default), the base layout, a real example document
  with no personal data, no unsaved dots, no error badges unless the shot is about
  errors. Window title and top bar visible.
- **Content.** Sample text is plain and neutral. No lorem ipsum, no faked
  names, no private paths, no real keys, no usernames. Clear recent-project
  lists.
- **No decoration.** No drop shadow, no rounded window frame, no browser or
  device mockup, no gradient or coloured backdrop, no annotation arrows in
  colours that are not the lime. If an annotation is needed, use one lime
  `2px` square outline and a mono label.
- **Compression.** Optimise PNGs losslessly; stay under 300 KB where the content
  allows. Store in the repo's `docs/screenshots/`, named
  `<what-it-shows>.png` in lower-case kebab.
- **Alt text and caption.** Alt text says what the screenshot shows. The caption
  names the version.
- **Refresh.** A screenshot is retaken when the UI it shows changes. A stale
  screenshot is removed rather than left.
- **Demos.** Prefer a short silent loop under 15 seconds or a still. If a demo is
  a video: 1440 × 900 or 1920 × 1080, 30 fps, no cursor flourishes, no music, no
  zoom effects, captions in DM Sans on a base-colour bar, and a transcript. A
  demo never autoplays with sound, and on the web it respects reduced motion by
  showing the still.
- **Tooling.** Capture with a headless browser or the OS screenshot tool at a
  fixed window size, so the next capture matches this one.

---

## 25 · Social images

- Sizes are in [`tokens.md`](./tokens.md#images-and-social-sizes): Open Graph
  1200 × 630, X banner 1500 × 500, LinkedIn banner 1584 × 396, Facebook banner
  820 × 312, avatars square.
- Build every image from an SVG source in `brand/exports/` and render the PNG
  from it. Never edit a PNG.
- Base `#141416`, a 1px hairline construction grid if any, the mark or lockup
  with one mark height of clear space, one headline in DM Sans 300 at −3%, one
  line of mono metadata, one lime element. Square everything.
- Keep the key content inside the central 80% of the width and the central 60%
  of the height: platforms crop banners differently, and a profile image covers
  the lower left of an X banner.
- Text is at least 24px in a 1200-wide image, and never lime on anything but the
  base.
- Product images use the product's mark and the same layout; the lab's credit is
  the line `Made by Fundaments.work` at the bottom end.
- Alt text is written wherever the platform has a field for it.
- Release graphics are the same card with the version in mono. No "NEW!" badges,
  no confetti, no emoji.

---

## 26 · Email

Email clients override almost everything, so the rules are about what must
survive.

- **Plain text first.** Send a `text/plain` part for every message, and write it
  to be complete on its own.
- **Width and layout.** 600px wide, single column, tables for layout, inline CSS.
  No web fonts, no JavaScript, no forms, no background images.
- **Colour.** Base `#141416` body, text `#e8e6e1`, links underlined in lime.
  Clients that invert or strip colours must still be readable, so set text and
  background together and never rely on the background alone.
- **Type.** DM Sans cannot be relied on, so the stack is
  `"DM Sans", "Helvetica Neue", Helvetica, Arial, sans-serif`, weight 400 (300
  is not safe), 16px body, 1.5 line height. Mono for versions and codes:
  `"DM Mono", ui-monospace, Menlo, Consolas, monospace`.
- **One action.** One lime button per message, a table cell with a solid
  background, 48px high, square. Under it, the same link as plain text.
- **Images.** The mark at the top, 40px high, with alt text `Fundaments.work`.
  Images off must still read. No tracking pixels, ever; do not link to a
  tracking redirect.
- **Content.** Voice per [section 9](#9--voice-and-copywriting). Subject lines are
  sentence case, under 50 characters, no emoji, no "Re:" tricks, no ALL CAPS.
  The first line says why the message exists.
- **Footer.** Who sent it and why the person is receiving it, a real postal or
  contact route, how to stop, and `Made by Fundaments.work`.
- **Transactional only by default.** The lab does not send marketing mail to
  people who did not ask for it. A newsletter is double opt-in and says how to
  leave in every message.
- **Test.** In the common clients at 375px, with images off, and in dark mode.

---

## 27 · Adding a new product

Do the checklist in order. Each item is a rule above, not a new one.

### Decide

- [ ] The product runs on a surface in [section 8](#8--surfaces). If it is a plugin
  for someone else's app, apply [section 19](#19--obsidian-plugins) and stop.
- [ ] It is an independent tool: offline, no server dependency, no telemetry,
  data in open formats ([Proposing a new tool](#proposing-a-new-tool)).
- [ ] It has a name that follows [Names](#names), not "Fundaments X".

### Identity

- [ ] A mark on a 24-unit grid, square, radius 0, legible at 14px, drawn from
  rectangles ([section 2](#2--marks)). Add it to `brand/marks/` with a favicon.
- [ ] Lockup with the credit line, and a mark-alone icon ([section 3](#3--lockup-and-names)).
- [ ] App icon master and rasters ([section 23](#23--app-icons-and-installers)).
- [ ] Open Graph card, social image and a GitHub social preview ([section 25](#25--social-images)).
- [ ] Badge SVGs only where a claim is true ([section 7](#7--collaboration)).
- [ ] Add the product to the brand files and to the downloadable bundle.

### Tokens

- [ ] Take the base and the accent unchanged. Add no hue ([`tokens.md`](./tokens.md)).
- [ ] Define the product's tokens as slots (`--bg`, `--surface`, `--accent`...), not
  as a private palette, in one stylesheet.
- [ ] Radius 0 backstop and a no-shadow rule in the global CSS.
- [ ] DM Sans 300/400 and DM Mono 400, self-hosted, with a font-weight backstop.
- [ ] Add a row to the Adoption status table and every deviation to Known drift.

### Surfaces

- [ ] Marketing page ([section 16](#16--marketing-sites)) with one primary action, copy from data files.
- [ ] Docs in the product repo, synced to the docs site as a product section
  ([section 17](#17--docs-sites)) with overview, guide, changelog.
- [ ] README per [section 21](#21--readmes-badges-and-github-repositories), repository settings, topics,
  issue forms, security policy.
- [ ] Changelog and the release workflow ([section 22](#22--release-notes-and-changelogs)),
  with checksums.
- [ ] Install paths: installers or a script ([section 20](#20--cli-terminal-output-and-install-scripts)),
  with an uninstall.
- [ ] Screenshots per [section 24](#24--screenshots-and-demo-capture).

### Verify

- [ ] Contrast measured for every text and control pair the product adds
  ([section 10](#10--accessibility)).
- [ ] Keyboard only: reach and operate every control, see the focus ring everywhere.
- [ ] Reduced motion on: nothing slides, nothing is lost.
- [ ] 375px and 1440px captures read cleanly (web); 640 × 480 and 1280 × 820 (app).
- [ ] No third-party requests: open the network panel and check.
- [ ] Every claim in the copy is true of the build.

---

## 28 · Decisions

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
| Clear space | Mark height, or the old aperture's nucleus diameter | One mark height for every mark | One rule, not two |
| Lemma | Inherits Obsidian by accident | Out of scope, inherits Obsidian by decision | It runs inside someone else's app |
| Collaboration terms | Badges only | Allowed, ask first, not permitted | Third parties need to know the boundary |
| Surfaces | Marks, colour and type only | Rules for sites, docs, apps, plugins, CLI, repos, releases, icons, screenshots, charts, email and new products | Every thing the lab ships needs one answer, not a guess |
| Error colour | None | `--danger`, errors and destructive actions only, always with an icon and a label | Contrast and meaning need a hue the accent cannot be; it is not a second accent |
| Success and warning colour | None | None; text colour with a check or a `!` and a label | Colour alone never carries state |
| Syntax colour | Per tool | Text, secondary, muted italic, sage and lime links, from Manang's editor | One accent stays one signal in code |
| Charts | Per tool | Lime for the series that matters, neutrals for the rest, up to five series | The highlight colours are content, not chart palette |
| Pie and donut charts | Per tool | Not used | They need circles and hues |
| Android and iOS icon masks | Not specified | Full-bleed square master; the platform cuts it | Corners on the user's screen are the platform's |

### Still open

- **Highlight labels.** The colours are fixed; Theorem's runtime labels
  them Important / Key Idea / Interesting / Critical / Action / Beautiful
  while this document says Core thesis / Method / Agreement or fact / Quote
  / Question / Contradiction. One canonical set is needed.
- **Lemma** has no mark on the 24 grid.
- **macOS icon shape.** Whether the macOS icon bakes in the system's template
  shape or ships a full-bleed square. Today: full-bleed square; revisit when a
  macOS build is released.
- **`--danger` and the chart palette** are specified and adopted nowhere. The
  first product to ship them should confirm the values on real screens.
- **A mono 300 use.** Large mono display text is allowed but nobody ships it.
- **Terminal accent in 256-colour terminals.** The rules give truecolor and
  16-colour values; a nearest 256-colour value is not chosen.
- **Licensing.** Whether MIT and CC-BY 4.0 cover the marks is unverified.
  The assumption here is that they do not.

### Sources

- [Fundaments.work design system](https://fundaments.work/docs/design-system/)
- [Theorem brand guidelines](https://theorem.fundaments.work/brand/)
- Manang's `src/app.css`, `DESIGN.md`, editor theme and `scripts/install-linux.sh`, and the landing site's `global.css` and `docs.css`, read 2026-10-19
- Theorem's `design-tokens.css` and `design-tokens.ts`, read 2026-10-11

---

## 29 · Adoption

How each product gets onto the system. No build step; this is a read and
an edit.

### Theorem

On the system. Dark is the default, lime is the default accent, the
sidebar is a fixed rail, and weights are 300 and 400. Its `design.md` is a
pointer to this repository. Still open: settle the highlight labels in
`design-tokens.ts`.

### Manang

On the system for base, radius, type and motion. Still to do: move secondary
and muted text to `#a0a0a0` and `#929292`, draw the focus ring at 2px, and name
`--danger` and the chart slots when it first needs them. Its `DESIGN.md`
describes the desktop shell this document generalises in
[section 18](#18--desktop-apps).

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