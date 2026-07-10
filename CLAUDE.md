# CLAUDE.md — Agency OS: Master Instructions

This repo is both a live project (a demo site for "GreenScape Landscaping,"
Greensboro NC) **and** the template/operating system for an AI-assisted web
agency that builds premium websites for local service businesses (landscapers,
contractors, cleaners, HVAC, salons, etc.). Read this file first; it points to
the four playbooks that govern design, SEO, conversions, and mobile quality.

## Agency Standards (non-negotiable, every project)

Every site built from this template — demo or paid client work — must:

1. **Look premium and modern.** No generic template feel, no default
   Bootstrap/stock look. See `DESIGN.md`.
2. **Be mobile-first.** Designed and tested at phone width first, desktop
   second. See `MOBILE.md`.
3. **Load quickly.** Fast first paint, no unnecessary weight. See
   `MOBILE.md` → Performance.
4. **Be SEO optimized.** Metadata, structured data, local SEO basics in
   place before launch. See `SEO.md`.
5. **Include strong trust signals.** Real reviews/testimonials, credentials,
   years-in-business, service guarantees — visible, not just claimed. See
   `CONVERSIONS.md`.
6. **Focus on generating leads.** Every page has a clear next action; the
   contact form actually delivers leads somewhere. See `CONVERSIONS.md`.
7. **Be good enough to sell for $1,000+.** This is the bar for "done." If a
   reasonable local business owner wouldn't pay four figures for it, it's not
   ready to show a client. Use this as the tiebreaker whenever unsure how
   much polish is "enough."

Treat these seven as a pre-launch checklist, not aspirational language — each
playbook below ends with a checklist that maps back to one or more of these.

## What this repo is, concretely

A static, no-build 4-page marketing site: `index.html`, `services.html`,
`gallery.html`, `contact.html`. Currently deployed as a **portfolio/demo** —
the owner uses it to show prospective landscaping clients what's possible.
It is not a real business; all contact info, stats, and reviews are
placeholders (tracked as open items in `CONVERSIONS.md`).

## Stack

- Plain HTML, one file per page — no JS framework, no CMS.
- Styling via the **Tailwind CDN JIT compiler** (`cdn.tailwindcss.com`) for
  speed of iteration during the demo/pitch phase — no build step, no
  `node_modules`. Each page has its own inline `tailwind.config`; keep all
  pages in a project in sync (see `DESIGN.md`). **This is a demo-phase
  shortcut, not the standard for a sold client site** — see `MOBILE.md` →
  Performance for when/how to compile Tailwind properly before final
  delivery.
- Fonts: Google Fonts, loaded via `<link>`, plus Material Symbols Outlined
  for icons. Swap the specific font pairing per client (see `DESIGN.md`).
- Images self-hosted in `images/` per project. Never hotlink a design tool's
  temporary preview CDN (e.g. `lh3.googleusercontent.com`) into anything
  meant to stay live — those URLs expire without warning.
- Small vanilla `<script>` blocks per page for interactivity: scroll fade-ins,
  mobile menu toggle, filters, accordions. No dependency needed for this
  level of interactivity.

## Deployment

- Hosted on **Vercel**, connected via GitHub — every push to `main`
  auto-deploys. This project: `adaobinwobu62-glitch/dobi-greenscape` →
  https://dobi-greenscape.vercel.app
- Standard flow for a new client project: new GitHub repo → `vercel git
  connect` (or import via the Vercel dashboard) → auto-deploy on push. Don't
  buy a custom domain until there's a paying client attached to the project —
  see the "new project" workflow below.
- Local preview: `python3 -m http.server 8080` from the repo root.

## Workflow: starting a new client project from this template

1. **Clone this repo structure**, not its content. Keep: page architecture,
   JS interaction patterns (filter, accordion, mobile menu, scroll fade-in),
   the five-file documentation system (this file + the four playbooks).
   Discard: GreenScape-specific colors, copy, images, business info.
2. **Interview the client** (or infer from their existing branding) for: to
   what feeling should the site aim (see `DESIGN.md` → Brand Voice
   Archetypes), primary service categories, service area/city, existing
   photography (always prefer real photos over stock — see `DESIGN.md` →
   Imagery), and what "success" means for the lead form (calls? bookings?
   quote requests?).
3. **Rewrite `DESIGN.md` first**, before touching code — pick a palette,
   type pairing, and brand voice for this client. Every other file should
   follow from it.
4. **Build pages**, applying `DESIGN.md` tokens consistently across every
   page's `tailwind.config` block.
5. **Wire up conversions** per `CONVERSIONS.md` before calling it done — a
   site with a non-functional contact form is not sellable.
6. **Run the `MOBILE.md` checklist** and the `SEO.md` checklist before
   handoff.
7. **Re-verify against the seven Agency Standards above** as the final gate.

## Working conventions

- **Don't reintroduce a build step** (Vite/Next/webpack) during the
  demo/pitch phase unless asked. Do plan to compile Tailwind for real,
  paid client delivery (flagged in `MOBILE.md`).
- **Keep every page's `tailwind.config` block identical within a project.**
  Token drift between pages is the most common bug in this workflow — check
  for it explicitly before declaring a project done.
- **Don't hotlink external images**, ever, in anything meant to stay live.
- Content (nav, footer, contact info) is duplicated per page by design —
  there's no shared partial without a build step. When updating shared
  content, grep across all HTML files, don't rely on memory.
- Never fabricate real-looking contact info in an actual client deliverable
  — placeholders are fine in a demo (clearly a demo), not in something a
  client will publish.

## The playbooks

- **`DESIGN.md`** — Design Standards, brand-voice archetypes, and this
  project's applied design system as a worked example.
- **`SEO.md`** — Local-SEO checklist: metadata, structured data, Google
  Business Profile, NAP consistency.
- **`CONVERSIONS.md`** — Trust signals, lead-capture patterns, CTA hierarchy,
  and this project's open gaps.
- **`MOBILE.md`** — Mobile-first process, performance budget, and the
  device/browser testing checklist.
