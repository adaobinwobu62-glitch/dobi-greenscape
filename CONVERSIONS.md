# CONVERSIONS.md — Lead Generation Playbook

Every site built from this template exists to generate leads for a local
service business — not to win design awards. This file is the checklist for
Agency Standards #5 (trust signals) and #6 (lead generation) from
`CLAUDE.md`. The current project's open gaps are listed at the bottom as a
worked example of what "not launch-ready" looks like.

## Above-the-fold requirements

Every page's first screen must answer, in under 3 seconds: *what does this
business do, where, and how do I contact them?*

- One clear, benefit-driven headline (not a company slogan/tagline that
  requires context to understand).
- One primary CTA button, visually dominant (see `DESIGN.md` → primary
  button spec), never competing with a second CTA of equal visual weight.
- Phone number visible in the nav or hero on every page, not buried in the
  footer only — service businesses get a meaningful share of leads from
  someone tapping to call directly, especially on mobile.

## Trust signals (must be real, not just claimed)

A stat or claim with no visible backing (e.g. "200+ Happy Customers" with no
reviews shown anywhere) actively hurts credibility once a visitor notices the
mismatch. For every trust claim on the site, there must be supporting
evidence on the site:

- **Testimonials/reviews** — at minimum 3–4 real quotes with a name (and
  ideally a photo or neighborhood/city). Pull from Google/Yelp reviews once
  the business has them; don't fabricate.
- **Credentials** — licensed/insured badges, years in business, certifications
  — stated plainly, not just implied by design polish.
- **Real photos of real work** — see `DESIGN.md` → Imagery Rules. This is
  simultaneously a design requirement and the single strongest trust signal
  available to a service business.
- **Specificity beats generality** — "Serving Lindley Park, Fisher Park, and
  Westerwood since 2009" reads as more credible than "Serving the whole
  metro area."

## Lead capture

- **The contact form must actually deliver leads somewhere** — a form with
  no backend is worse than no form; it silently loses every visitor who
  tries to convert. For a static site with no backend of its own, use a
  form-endpoint service (e.g. Formspree, Web3Forms) or a Vercel serverless
  function — either is a five-minute integration, not a reason to skip it.
- **Confirm on submit.** After a successful submission, show a clear
  success state (inline message or a `/thank-you` page) — never leave the
  user wondering if it worked.
- **Keep the form short.** Name, phone, email, service type, brief message
  is the ceiling for a local-service lead form. Every additional required
  field measurably reduces completion rate.
- **Offer a second path.** Not everyone wants to fill out a form — a
  tap-to-call (`tel:`) link and/or a direct email link should exist
  alongside the form, not instead of it.
- **Track submissions.** At minimum, know that leads are arriving (email
  notification from the form service). For a serious client site, add
  analytics (see below) so the client can see traffic → lead conversion
  rate over time.

## CTA hierarchy

- One consistent primary CTA phrase/action across the site (e.g. "Get a
  Free Estimate") — don't rotate between different asks on different pages,
  it dilutes the funnel.
- Repeat the primary CTA at every natural decision point: nav bar, hero,
  end of services section, end of the page. A visitor should never have to
  scroll far to find the next step.
- Secondary CTAs (e.g. "View Our Work," "Learn More") are fine but should
  always be visually subordinate to the primary action.

## Analytics & tracking (for real client delivery)

- Google Analytics 4 (or a privacy-friendlier alternative like Plausible) at
  minimum, so the client can see traffic.
- Event tracking on: form submissions, `tel:` link clicks, and outbound
  clicks to booking tools if any exist.
- If budget/lead volume justifies it, call tracking (a tracked phone number)
  tells the client which channel (site vs. Google Business Profile vs.
  referral) is actually producing calls.

---

## Current status — GreenScape Landscaping (demo project)

This is a **demo**, so the following are expected placeholders — listed here
so they're not forgotten if this project is ever adapted into someone's
actual live client site:

- ✅ **Contact form has a real backend.** Both the contact-page form and the
  homepage quote form POST to FormSubmit
  (`https://formsubmit.co/ajax/adaobinwobu62@gmail.com`), with a JS handler
  that shows inline success/error state instead of a page reload. Before
  handing this off as a real client site, swap the destination address to
  the client's own inbox — right now every submission lands in the demo
  owner's personal email.
- ❌ **All contact info is fake** (`(336) 555-0123`, `123 Friendly Ave`,
  `hello@greenscapegso.com`) — placeholders only, not to be used as-is.
- ✅ **Testimonials section exists** (`index.html#testimonials`, linked from
  nav on every page) — 3 named reviews with neighborhood/rating, which is
  what backs the "200+ Happy Friends & Families" stat. No longer an
  unsupported-claim mismatch.
- ❌ **No analytics installed.**
- ❌ **No "Designed by" credit or lead-gen CTA pointing back to the site's
  actual owner** — since this demo's purpose is to win the owner new
  clients, the demo itself currently captures none of its own leads.
- ✅ Gallery filter buttons are functional (fixed from an earlier no-op
  state).
- ✅ Images are self-hosted (fixed from hotlinking a temporary preview CDN).
- ✅ FAQ accordion, mobile nav, and tap-to-call links are functional.
- ✅ Contact page has a real embedded Google Map (fixed from a blank
  placeholder box).
- ✅ Form labels are programmatically associated with their inputs
  (`id`/`for` pairs) and FAQ accordion buttons have a visible focus state —
  both were silent screen-reader/keyboard-nav gaps, fixed in an
  accessibility pass.
