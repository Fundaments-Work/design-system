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
| Mono | Ink `#1a1a1a` | — | Theorem only, one colour |

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

Raster derivatives for social and web. These are **generated from the
current typography**, which the system has since changed — see the note
below.

- `exports/og-1200x630.png`
- `exports/theorem-social.png`
- `exports/banner-{x-1500x500,linkedin-1584x396,facebook-820x312}.png`
- `exports/avatar-{128,200,320,400,512,800,1024}.png`

---

## Known drift in these files

Recorded so it is not rediscovered. None of it is fixed yet — fixing any
of it changes a shipped asset and needs a decision.

| File | Issue |
|---|---|
| `theorem-logo.svg` | Fill is `#0a0a0a`. The system token is Ink `#1a1a1a`. |
| `theorem-app-icon.svg` | Fill is `#0a0a0a`, and the field carries `rx="100"` — the only rounded corner anywhere in the brand kit, against the zero-radius rule. Its mark is `#fafaf8`; the system paper is `#ffffff`. |
| `fundaments-badge.svg`, `telemetry-badge.svg` | Field is `#1e221b`, which matches no token. The nearest is a carbon step at `#1e201b`. |
| `exports/*.png` | Rasterised in Inter. The system now specifies DM Sans, so these are stale until regenerated. |