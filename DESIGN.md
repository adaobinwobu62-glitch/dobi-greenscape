# DESIGN.md — Design Playbook

Design standards for every site built from this template, plus the specific
design system implemented for the current project (GreenScape Landscaping,
Greensboro NC) as a worked example. When starting a new client project,
rewrite everything below "Applied Design System" — the standards above it are
durable across every project.

## Design Standards (every project)

1. **Large hero sections.** The first screen a visitor sees should be a full,
   confident statement — a large image/photo, a short bold headline, one
   clear CTA. Never a cramped, text-heavy hero.
2. **Strong typography.** A deliberate two-font pairing (one display/headline
   face with character, one highly-legible body face) — never the system
   default stack, never more than two families.
3. **Consistent spacing.** One 8px-based spacing scale, applied everywhere.
   No one-off pixel values invented mid-build. If a page "feels off," check
   for spacing scale violations first.
4. **Premium color palettes.** A restrained palette (one primary, one accent,
   one or two neutrals, all in service of a specific mood) — not five
   unrelated brand colors. See the palette formula below.
5. **Professional imagery.** Real photography of the actual business/work
   whenever possible. If real photos aren't available yet (early pitch/demo
   stage), use high-quality stock or AI-generated placeholders that are
   internally consistent in lighting and style — never mismatched stock.
6. **Smooth animations.** Subtle scroll-triggered fade-ins, hover states with
   gentle scale/opacity transitions (100–300ms), never jarring or bouncy.
   Motion should feel like polish, not a distraction.
7. **Modern layouts.** Asymmetric grids, bento-style card arrangements,
   generous whitespace — avoid the dated "centered stack of equal-width
   boxes" look.

## Brand Voice Archetypes

Pick one deliberately per client — it should drive color, type, and copy
tone together, not be chosen piecemeal:

- **Trusted Local Neighbor** — warm, approachable, community-rooted. Rounded
  type, warm off-white backgrounds, earthy/warm accent colors. (Used for the
  current project — see below.)
- **Premium/Editorial Authority** — quiet luxury, architectural precision.
  Serif display font, tight letter-spacing, crisp white/deep-tone palette,
  minimal ornamentation, generous negative space.
- **Bold & Energetic** — for younger-skewing or high-energy services
  (fitness, events). Saturated accent color, punchy sans-serif, higher
  contrast, faster/snappier animation timing.

Don't mix archetypes within one project — every token decision below should
trace back to the one chosen.

## Color Palette Formula

For any new client:

1. Pick **one primary** (usually a dark, saturated version of a brand-relevant
   color — forest green for landscaping, navy for professional services,
   etc.) — used for headlines, nav, primary surfaces.
2. Pick **one accent** in a contrasting hue/warmth for CTAs specifically, so
   buttons are unmistakable against the primary.
3. Pick **one neutral background** that is *not* pure white (a warm or cool
   off-white depending on archetype) — pure white reads as generic/cheap next
   to a considered palette.
4. Derive `on-*` (text-on-color) pairs for every surface color, and
   light/dark "container" variants of primary/accent for badges, chips, and
   hover states. This is the Material-3-style token structure used
   throughout this codebase — see the applied example below.

## Typography Scale

Regardless of which fonts are chosen, keep a scale with roughly these steps
(desktop / mobile sizes shown as the current project's example — adjust
values per archetype, keep the *step count and ratio* similar):

`headline-xl` (hero, ~48px) → `headline-lg` (section titles, ~32px) →
`headline-md` (card titles, ~24px) → `body-lg` (intros, ~18px) → `body-md`
(default body, ~16px) → `label-md`/`label-sm` (buttons, eyebrow text,
uppercase + letter-spaced, ~14px/12px).

## Shape & Spacing

- One border-radius scale (e.g. `sm` 0.25rem → `full` 9999px) applied
  consistently — cards typically get the larger end, buttons the smaller end
  or fully pill-shaped depending on archetype.
- One 8px-based spacing scale. Section vertical padding should be generous
  (64–120px) to avoid a cramped, transactional feel.
- Shadows should be soft, diffused, and tinted with the primary color —
  never default pure-black box-shadows. This alone is one of the highest-
  leverage "does this look premium" signals.

## Imagery Rules

- Self-host every image (see `CLAUDE.md` → Working conventions). Never ship
  a client site hotlinking a temporary preview CDN.
- Keep lighting/color-grade consistent across all photos on a page — a mix
  of warm and cool stock photos is one of the fastest ways to look
  unprofessional.
- Real project/team photos outrank any stock or AI-generated placeholder
  once the client can provide them — flag this explicitly as an open item
  in `CONVERSIONS.md` if using placeholders.

---

## Applied Design System — GreenScape Landscaping (current project)

Implemented identically in the `tailwind.config` block of all four pages.
Archetype: **Trusted Local Neighbor.**

### Colors

| Token | Hex | Use |
|---|---|---|
| `primary` | `#154212` | Headlines, nav active state, footer bg, primary buttons |
| `secondary` | `#805600` | Accents, links on dark backgrounds |
| `secondary-container` | `#fdba49` | Primary CTA buttons (goldenrod) |
| `tertiary` | `#64250f` | Secondary accent icons (terracotta) |
| `background` / `surface` | `#fbf9f4` | Page background (warm off-white, not pure white) |
| `surface-container-low` | `#f5f3ee` | Card/section backgrounds |
| `on-surface` | `#1b1c19` | Body text |
| `on-surface-variant` | `#42493e` | Secondary/muted text |
| `outline-variant` | `#c2c9bb` | Borders |

Full token list (all Material-3-style `on-*` / `*-container` pairs) is in the
`tailwind.config.theme.extend.colors` block — copy it verbatim into any new
page within *this* project rather than retyping. For a new client, regenerate
per the palette formula above.

### Typography

- **Headlines:** Baloo 2 (600–800 weight) — rounded, hand-lettered warmth,
  friendly rather than authoritative.
- **Body/labels:** Work Sans (400–600 weight).

### Shape & Spacing

- Border radius: `sm` 0.25rem, `DEFAULT` 0.5rem, `md` 0.75rem, `lg` 1rem,
  `xl` 1.5rem, `full` 9999px. Cards use `lg`/`xl`; buttons use `DEFAULT`/`full`
  (pill buttons for primary CTAs).
- Spacing: `xs` 4px, `sm` 12px, `md`/`gutter` 24px, `lg` 48px,
  `xl`/`section-padding` 80px, `margin-mobile` 16px / `margin-desktop` 64px.
- Shadow: `warm-shadow` utility — `0 10px 30px -5px rgba(21, 66, 18, 0.1)`.

### Components

- **Primary button:** `bg-secondary-container` (goldenrod) + dark text,
  pill-shaped, min-height 48px.
- **Secondary button:** transparent with 2px `border-primary` or
  `border-tertiary`.
- **Cards:** `bg-surface` or `bg-surface-container-low`, `rounded-xl`, thin
  `outline-variant/30` border, `warm-shadow`.
- **Nav:** fixed, blurred translucent background, pill CTA button, active
  link underlined in secondary color.
- **Icons:** Material Symbols Outlined throughout — don't mix icon sets.

### History note

The original three Stitch-exported source pages (home/services/gallery) each
shipped a slightly different `borderRadius` scale. The version above is the
reconciled single source of truth — if you ever see a fourth variant creep
in, treat it as a bug, not a new option.
