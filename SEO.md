# SEO.md — Local SEO Playbook

The local-SEO checklist for every site built from this template, plus the
current status of this project (GreenScape Landscaping) as a worked example.
Every item under "Before a real client site launches" is a launch gate, not
a nice-to-have — a client site without them is not meeting the SEO-optimized
bar in `CLAUDE.md` → Agency Standards.

## General principle

Local-service SEO is 20% on-page (metadata, structured data) and 80%
off-page (Google Business Profile, reviews, NAP consistency, backlinks from
local directories). Don't over-invest in the on-page 20% at the expense of
the checklist below — both matter, but the off-page work is usually what
actually moves ranking for a landscaper, plumber, or salon.

## Current state (as of this demo)

- **No `<meta name="description">` on any page.** Google will fall back to
  scraping visible text for the search snippet — unpredictable.
- **No Open Graph / Twitter Card tags.** Links shared in text messages,
  iMessage, Slack, or social media currently show no preview image or
  description.
- **No favicon.** Browser tabs show the generic globe icon.
- **No `sitemap.xml` or `robots.txt`.** Not critical at 4 pages, but expected
  by convention and by some crawlers/tools.
- **No `LocalBusiness` structured data (JSON-LD).** This is the single
  highest-leverage local-SEO addition for a landscaping business — it's what
  lets Google show a business panel (hours, phone, service area, rating)
  directly in search results.
- **Titles exist and are reasonable** per page (e.g. "Our Services |
  GreenScape Landscaping Greensboro") — descriptive, includes the brand and
  city, under ~60 characters.
- **Images have descriptive `alt` text** already (carried over from the
  original design export) — good for image search and accessibility, no
  change needed there.
- **Semantic HTML is mostly solid** (`<nav>`, `<main>`, `<footer>`, one `<h1>`
  per page) — no major structural fixes needed.

## Before a real client site launches, add:

1. Per-page `<meta name="description">` (~150–160 characters, unique per
   page, includes the service + city).
2. Open Graph tags (`og:title`, `og:description`, `og:image`, `og:url`) and
   `twitter:card` — reuses one of the hero images as the share image.
3. A real favicon (`favicon.ico` + `apple-touch-icon.png`), matching the
   brand mark.
4. `LocalBusiness` JSON-LD in the footer of every page, with real: business
   name, address, phone, hours, service area, and (once they exist) review
   aggregate data.
5. `sitemap.xml` listing all pages + `robots.txt` pointing to it.
6. Register the business with **Google Business Profile** — this matters
   more for local landscaping SEO than almost anything on the site itself.
   The website supports the Business Profile; it doesn't replace it.
7. Confirm NAP (Name/Address/Phone) is byte-for-byte identical across the
   site, the Business Profile, and any directory listings (Yelp, Nextdoor,
   Angi) — inconsistency actively hurts local ranking.

## Not worth doing for a small local-service site

- Heavy technical SEO tooling, an XML sitemap index, hreflang, or a blog/CMS
  — overkill for a 4-page landscaping site. Time is better spent on the
  Business Profile and getting real reviews than on SEO plumbing.
