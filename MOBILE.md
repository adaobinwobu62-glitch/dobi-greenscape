# MOBILE.md — Mobile-First Playbook

Most visitors to a local service business's site are on a phone, often on a
mediocre connection, often while standing outside looking at the exact
problem they need help with. This file is the checklist for Agency Standards
#2 (mobile-first) and #3 (loads quickly) from `CLAUDE.md`.

## Mobile-first process

- Design and review at **375px width first**, then check tablet (~768px),
  then desktop. Never design desktop-first and "make it responsive" after —
  that produces cramped, afterthought mobile layouts.
- This codebase's pattern: a single `md:` breakpoint (768px) switches most
  layouts from stacked/mobile to multi-column/desktop. Simple and
  sufficient for a 4-page marketing site — don't over-engineer with five
  breakpoints unless a specific layout actually needs it.

## Touch targets & readability

- Minimum touch target size: **48x48px** (matches the `min-h-[48px]` used on
  buttons throughout this project). Anything smaller is a mis-tap risk,
  especially on a CTA button.
- Body text minimum **16px** — smaller forces zooming, which tanks mobile
  usability scores and, more importantly, annoys real visitors.
- Adequate spacing between adjacent tappable elements (nav links, footer
  links) so a thumb can't easily hit the wrong one.
- Confirm `<meta name="viewport" content="width=device-width,
  initial-scale=1.0">` is present on every page (it is, in this project) —
  without it, mobile browsers render at desktop width and shrink, which
  breaks everything.

## Mobile navigation

- Hamburger menu with a visible, high-contrast icon; opens a full-width
  panel (not a cramped dropdown) with the same links as desktop nav, plus
  the primary CTA repeated at the bottom of the panel. This project's
  pattern (`#mobile-menu` toggle) follows this and should be reused as-is.
- Consider a **sticky mobile call bar** (persistent bottom bar with "Call
  Now" / "Get Quote") for real client sites — this single pattern often
  outperforms every other mobile conversion tactic for local-service
  businesses, since a phone call is the lowest-friction conversion on a
  phone. Not yet implemented in this demo — see `CONVERSIONS.md`.

## Performance budget

- **Images:** self-hosted, reasonably sized (this project's are ~60–90KB
  each, fine for a 4-page site). For a real client site with more/larger
  imagery, compress and serve responsive sizes (`srcset`) so mobile doesn't
  download a desktop-sized hero image over cellular.
- **Tailwind CDN JIT is a demo-phase shortcut, not a production pattern.**
  It ships the full Tailwind compiler to the browser and compiles CSS
  client-side on every page load — noticeably heavier and slower than a
  precompiled stylesheet. **Before delivering any real, paying client site,
  replace it with a compiled Tailwind build** (a one-time `npx
  tailwindcss -o styles.css --minify` step, still no framework required) —
  this is the single biggest performance gap between this demo and a
  sellable deliverable.
- **No render-blocking heavy JS.** This project's vanilla `<script>` blocks
  are small and fine; don't add a JS framework or large dependency for a
  static marketing site.
- Target **Lighthouse mobile Performance score of 90+** before calling a
  client site done. Run it in Chrome DevTools (Lighthouse tab, Mobile,
  throttled) — not just the "Fast 3G" toggle, an actual throttled run.

## Testing checklist (run before every launch)

- [ ] Real phone, real cellular connection (not just wifi + DevTools
      emulation) — emulation misses real-world jank and font-loading flicker.
- [ ] Both iOS Safari and Android Chrome — they render fonts, form controls,
      and `backdrop-blur` differently often enough to matter.
- [ ] Rotate to landscape and confirm nothing breaks.
- [ ] Every button/link is tappable without zooming or mis-tapping a
      neighbor element.
- [ ] Forms: confirm the on-screen keyboard doesn't cover the submit button,
      and that input types (`tel`, `email`) trigger the right mobile keyboard.
- [ ] Lighthouse mobile run: Performance, Accessibility, SEO all 90+.
- [ ] No horizontal scroll at any width from 320px up.

## Current status — GreenScape Landscaping (demo project)

- ✅ Mobile menu, touch target sizing, and viewport meta are implemented
  correctly per the standards above.
- ⚠️ **Only verified via HTTP 200 checks, not actual visual/device
  testing** — the checklist above has not been run end-to-end on a real
  device for this project. Do this before showing the demo to anyone
  security- or detail-conscious.
- ❌ **No sticky mobile call bar.**
- ❌ **Still on the Tailwind CDN JIT compiler** — acceptable for a pitch
  demo, but must be swapped for a compiled build before this pattern is used
  on a real, paying client's site (see Performance budget above).
