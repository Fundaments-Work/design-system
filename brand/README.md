# Brand assets

Official files for every mark, badge and export. Use them unchanged.

**Layouts only.** Never redraw a mark, never type one as characters, never
round, rotate, skew or outline it, never place one on a gradient, photo or
drop shadow. The official SVG governs; values quoted in prose are for
reference only.

---

## Marks

| File | What it is |
|---|---|
| `fundaments-mark-lime.svg` | Lab mark with construction hairlines, transparent. For dark surfaces. The name is kept so the URL stays stable. |
| `fundaments-mark-carbon.svg` | Lab mark with construction hairlines, transparent. For light surfaces (ink and olive). |
| `fundaments-mark-mono.svg` | Lab mark, F and square only, in `currentColor`. One colour, any surface. |
| `fundaments-logo.svg` | Lab mark with hairlines on a full-bleed base `#141416`. |
| `fundaments-lockup.svg` | Lab mark plus the `Fundaments.work` wordmark, `.work` in grey. |
| `favicon.svg` | Lab mark without hairlines, cropped tight, on the base. |
| `theorem-favicon.svg` | Theorem's favicon: the T in Ink on the dark base, square. The source for every Theorem raster icon. |
| `theorem-logo.svg` | Theorem's turnstile, 24-unit grid. |
| `theorem-app-icon.svg` | Theorem's turnstile on a rounded app-icon field. |

### Geometry

**Lab mark** — 512 grid. The F: `M 144 112 H 368 V 160 H 192 V 400 H 144 Z`,
stem and cap 48 thick, no middle arm. The proof square: 48 × 48 at (240, 232),
centre (264, 256), where the missing middle arm would end. Construction
hairlines, 2 thick: a cross through the square's centre spanning 64–448, and a
brighter segment from the stem to x 336. Corner radius 0. The mark is the F and
the square; the hairlines are drawn at 64px and above and left out below.
The mark box (the F) is 224 × 288, centred at (256, 256).

**Theorem turnstile** — 24-unit grid: bar 16 × 4, stem 4 × 8, foot 4 × 4.
Corner radius 0. Minimum size 14px.

### Colourways

| Variant | Mark | Field | Use |
|---|---|---|---|
| Default | F `#e8e6e1`, square lime `#c6f135`, hairlines `#28282c` and `#7a7a7a` | Base `#141416` or none | Dark surfaces, social, OG |
| Reversed | F ink `#1c1c1c`, square olive `#4d6a00`, hairlines `#d4d3ce` and `#929292` | — | Light surfaces, print |
| Mono | `currentColor`, no hairlines | — | One colour: the lab's `fundaments-mark-mono.svg`, Theorem's ink |

### Clear space and size

One mark height of clear space on every side, for every mark. Minimum size
14px. Below that the Theorem foot closes against the stem.

---

## Badges

| File | Copy |
|---|---|
| `fundaments-badge.svg` | Built with Fundaments.work |
| `telemetry-badge.svg` | Zero Telemetry |
| `theorem-badge.svg` | Read on Theorem |
| `sync-badge.svg` | Syncs to Obsidian |

The Zero Telemetry badge only goes on a project that sends no telemetry.
The Obsidian badge names a third party — follow Obsidian's own terms
beyond it.

---

## Exports

Raster derivatives for social and web, rendered from the SVG sources that sit
next to them, in DM Sans and DM Mono at 300 and 400. Re-render a PNG from its
SVG whenever the SVG changes; never edit a PNG by hand.

- `exports/og-fundaments-1200x630.png` from `og-fundaments.svg`
- `exports/og-theorem-1200x630.png` from `og-theorem.svg`
- `exports/theorem-social.png` from `theorem-social.svg`
- `exports/banner-{x-1500x500,linkedin-1584x396,facebook-820x312}.png` from the matching `.svg`
- `exports/avatar-{128,200,320,400,512,800,1024}.png` from `marks/fundaments-logo.svg`

### Missing, specified in the guidelines

Not yet produced. Each is derived from an existing SVG; do not hand-draw them.

| Asset | Size | Rule |
|---|---|---|
| GitHub social preview | 1280 × 640 PNG, under 1 MB | [Guidelines 21](../guidelines.md#21--readmes-badges-and-github-repositories) |
| Email header | 1200 × 400 PNG (shown at 600 wide) | [Guidelines 26](../guidelines.md#26--email) |
| App-icon master, lab | 1024 × 1024 SVG, square | [Guidelines 23](../guidelines.md#23--app-icons-and-installers) |

---

## Known drift in these files

Recorded so it is not rediscovered.

| File | Issue |
|---|---|
| `theorem-logo.svg` | **Fixed.** Fill is now Ink `#1c1c1c`, the system token (was `#0a0a0a`). |
| `theorem-app-icon.svg` | **Fixed.** The field is square on the base `#141416` and the mark is `#e8e6e1` (was `rx="100"`, `#0a0a0a` and `#fafaf8`). |
| `fundaments-badge.svg`, `telemetry-badge.svg` | **Fixed.** The telemetry field is now the Surface token `#1c1c20` (was `#1e221b`, which matched no token). |
| `fundaments-lockup.svg` | **Fixed.** Set in DM Sans 300 on Ink (was Inter 600 on white). |
| `exports/*.png` | **Fixed.** Re-rendered from SVG sources in DM Sans and DM Mono. |
| `theorem-brand.zip` | Not served by fundaments.work; contents not checked against `marks/`. |
| `fundaments-brand.zip` | **Fixed.** Rebuilt with the new lab mark and copied unchanged to `fundaments-landing/public/brand/`. |
