# SEO & AI Bot Audit Report

> Orchestrated by: search-optimizer (evidence-dir `../../evidence`, skip-checks: `agent-readiness-scan`)

**Project:** tapioca-junction-site (worktree-s9-site)
**Framework:** generic static HTML (GitHub Pages project site under `/tapioca-junction-site/`)
**Files audited:** 4 / 4 HTML (index, support, privacy; 404 added in Step 6) · `scripts/audit_seo.py`
**Date:** 2026-11-17

Deployed copy check: the live `index.html` (evidence/page.html) is byte-identical to the committed one. The host
root (`nguyenvanlamm.github.io`, another repo) serves `robots.txt` (all bots allowed, `Content-Signal`, a `Sitemap:` line
per game site, none yet for this site) and `llms.txt` (one line per game site, none yet for this site); `/sitemap.xml`
at the host root is 404 (expected: each project site has its own).

Step 3 (web research) was not run: the run is limited to local files and the owner's own pages; the embedded
references (`technical-seo.md`, `ai-bot-guide.md`) were used.

## Before (audit script: 0 critical · 10 warning · 4 info)

### Critical
- none

### Warnings
1. [index.html:6] Title carries the reference genre term "marble-run" (4.3 guard, G4) — manual review.
2. [index.html:92] Hero copy "a little marble run you planned" — same term — manual review.
3. [index.html:7] Meta description 170 chars (> 160).
4. [index.html] No JSON-LD.
5. [index.html] `og:type`, `og:url` missing; `og:image` is a 390×844 portrait screenshot (cropped badly in 1.91:1 cards).
6. [support.html, privacy.html] No Open Graph tags, no JSON-LD.
7. [project] No `robots.txt` under the site path.
8. [project] No `sitemap.xml`.

### Info
1. [all pages] No Twitter Card tags.
2. [project] No `llms.txt`.
3. [project] No `.well-known/ai-plugin.json` (optional; not applicable to a static game page).
4. [all pages] Favicon is the 180 px icon; no root `apple-touch-icon.png` / small favicon.

### Manual review
- Facts vs the shipped game (G4): Full Menu now opens Cheese Foam order 1 at once and Late Night opens after Cheese
  Foam (`lib/game/progress.dart` `isOpen`); the pricing line and support "Purchases" did not say so.
- Footer "© 2026 Tapioca Junction" should name the seller, "Luong Nguyen" (`docs/APP-STORE-CONNECT.md` §1).
- Headings: one H1 per page, H2/H3 order fine; `lang="en"`, viewport, charset and canonicals present on all pages.
- Mobile: no horizontal scroll at 390 px (measured in headless Chrome).

## Plan (approved by the owner at G4 — applied without a further gate)

### Priority 1
- [x] Remove "marble-run"/"marble run" from title and hero; describe flippers, tubes and the route you set — index.html
- [x] Footer © 2026 Luong Nguyen — index.html
- [x] Full Menu facts (Cheese Foam order 1 at once; Late Night after Cheese Foam) — index.html, support.html
### Priority 2
- [x] Meta description ≤ 160 (now 147) — index.html
- [x] Open Graph (type, url, site_name, locale, 1200×630 share card + alt) and Twitter Card on all three pages
- [x] JSON-LD: `VideoGame`+`MobileApplication` (operatingSystem iOS, `creativeWorkStatus: Upcoming`, no offers, no
      rating), `WebSite`, `FAQPage` mirroring the visible FAQ — index.html; `WebPage` on support/privacy
- [x] `sitemap.xml` (three pages), `robots.txt` (site-path copy with AI bot directives + Sitemap), `llms.txt`
### Priority 3
- [x] `404.html` in the Night Signal style (noindex), `favicon.png` 48 px, `apple-touch-icon.png` 180 px from the
      1024 px app icon; hero served as WebP (28 KB) with PNG fallback; `rel=alternate` link to llms.txt

Offers: omitted on purpose. The app will be free with in-app purchases, but schema.org has no availability value for a
product that is not yet released, and the owner asked for no price claims beyond the IAP list.

## After (audit script: 0 critical · 6 warning · 2 info)

Remaining warnings are expected: `404.html` has no canonical/OG/JSON-LD (a noindex error page), and
`.reports/search-optimizer/evidence/page.html` is the pre-fix capture kept as evidence. `marble` occurs nowhere in
the site files. All JSON-LD blocks parse.

## Follow-up outside this repo
- Host root `nguyenvanlamm.github.io`: add `Sitemap: https://nguyenvanlamm.github.io/tapioca-junction-site/sitemap.xml`
  to `robots.txt` and a Tapioca Junction line to `llms.txt` (one chore commit, per the pipeline's S9 rule).

## Step 8
Skipped: the owner did not allow an outside agent-readiness scan (G4); `agent-readiness-scan` was passed in skip-checks.

Result: COMPLETE — audit, approved plan, implementation and validation done; Step 8 skipped by owner decision.
Evidence: scripts/audit_seo.py before 0/10/4 → after 0/6/2 (remaining are expected); JSON-LD parse check passed.
Uncertainty: Step 3 web research not run; rich-result eligibility not tested with Google's tools (outside service).
Decision: No approval needed.
