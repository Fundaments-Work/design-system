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
| `fundaments-mark-lime.svg` | Lab aperture, acid lime. The mark on dark surfaces. |
| `fundaments-mark-carbon.svg` | Lab aperture, carbon. The mark on light surfaces. |
| `fundaments-logo.svg` | Aperture on a full-bleed carbon field. |
| `fundaments-lockup.svg` | Aperture plus the `fundaments.work` wordmark. |
| `favicon.svg` | Aperture, carbon field, lime mark. |
| `theorem-favicon.svg` | Theorem's favicon: the T in Ink on the dark base, square. The source for every Theorem raster icon. |
| `theorem-logo.svg` | Theorem's turnstile, 24-unit grid. |
| `theorem-app-icon.svg` | Theorem's turnstile on a rounded app-icon field. |

### Geometry

**Lab aperture** — 512 grid, spine 52, arm 112, nucleus r 44 at
(256, 256). Corner radius 0.

**Theorem turnstile** — 24-unit grid: bar 16 × 4, stem 4 × 8, foot 4 × 4.
Corner radius 0. Minimum size 14px.

### Colourways

| Variant | Mark | Field | Use |
|---|---|---|---|
| Default | Lime `#c6f135` | Carbon `#12140f` | Dark surfaces, social, OG |
| Reversed | Carbon `#12140f` | — | Light surfaces, print |
| Mono | Ink `#1c1c1c` | — | Theorem only, one colour |

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
