# Search Optimization: Tapioca Junction site

Run: search-optimizer 1.1.0 · 2026-11-17T04:15Z · branch: web
Evidence: evidence/manifest.json · scan case: B (owner did not allow an outside scan at G4)
Members: seo-ai-optimizer √ · website-agent-readiness — skipped (owner did not allow an outside scan) · viral-product-evaluator √ (63/100, one run shared with design-optimizer; report in ../design-optimizer/reports/viral-product-evaluator/)

## Summary
- Agent-readiness score: not scanned (owner decision)
- SEO before: 0 critical · 10 warning · 4 info → after: 0 critical · 6 warning (expected: 404 page, pre-fix evidence copy) · 2 info
- Findings: 0 P0 · 4 P1 · 6 P2 · 2 P3, all fixed in this worktree except S-12 (host-root repo)

## Web findings

| ID | Pri | Check | Finding | Evidence | Owner | Also reported by | Fix route |
|---|---|---|---|---|---|---|---|
| S-01 | P1 | meta-tags | Title and hero used the reference genre term "marble-run" / "marble run" (4.3 guard, G4) | index.html:6, :92 | seo-ai-optimizer | G4 decision | applied: "a bubble-tea logic puzzle"; hero describes flippers and the route you set |
| S-02 | P1 | meta-tags | Footer named the game, not the seller | index.html:181 | seo-ai-optimizer | G4 decision | applied: "© 2026 Luong Nguyen" |
| S-03 | P1 | meta-tags | Pricing and support did not say Full Menu opens Cheese Foam order 1 at once and Late Night after Cheese Foam | index.html:147, support.html:34; game `Progress.isOpen` | seo-ai-optimizer | G4 decision | applied |
| S-04 | P1 | structured-data | No JSON-LD on any page | audit_seo.py | seo-ai-optimizer | — | applied: VideoGame+MobileApplication (iOS, Upcoming, no offers, no rating), WebSite, FAQPage; WebPage on support/privacy |
| S-05 | P2 | meta-tags | Meta description 170 chars | audit_seo.py | seo-ai-optimizer | — | applied (147) |
| S-06 | P2 | meta-tags | og:type/og:url missing; og:image a 390×844 portrait; no OG on support/privacy; no Twitter Card | audit_seo.py, head.json | seo-ai-optimizer | viral-product-evaluator #5 (PASS after fix) | applied: 1200×630 share card, OG + Twitter on all pages |
| S-07 | P2 | robots-sitemap | No sitemap.xml | audit_seo.py | seo-ai-optimizer | — | applied (three pages) |
| S-08 | P2 | crawler-access | No robots.txt under the site path (host root allows all) | evidence/robots.txt | seo-ai-optimizer | — | applied: site-path copy with AI bot groups + Sitemap |
| S-09 | P2 | llms-txt | No llms.txt | audit_seo.py | seo-ai-optimizer | — | applied |
| S-10 | P2 | meta-tags | Favicon was the 180 px icon; no apple-touch-icon file; no 404 page | index.html:9 | seo-ai-optimizer | — | applied: favicon.png 48, apple-touch-icon.png 180, 404.html (noindex) |
| S-11 | P3 | meta-tags | Hero image 276 KB PNG | assets/game.png | seo-ai-optimizer | — | applied: WebP 28 KB with PNG fallback |
| S-12 | P3 | robots-sitemap | Host-root robots.txt and llms.txt do not list this site yet | evidence/robots.txt, evidence/llms.txt | seo-ai-optimizer | ux-ax-review F5 | needs the nguyenvanlamm.github.io repo (one chore commit at S9) |

## Skipped (owned elsewhere)
| Check | Skipped by | Owner |
|---|---|---|
| meta-tags | viral-product-evaluator | seo-ai-optimizer |

## Not covered
| Check | Reason |
|---|---|
| agent-readiness-scan | Owner did not allow an outside scan (G4) |
| markdown-pages | Needs the scan; owner did not allow it |
| ai-actions | No web-branch member evaluates it; covered by the design-optimizer run (ux-ax-review: not applicable) |

## Member reports
- reports/seo-ai-optimizer/seo-audit-report.md
- ../design-optimizer/reports/viral-product-evaluator/viral-evaluation.md

## Next step
Add this site to the host-root robots.txt and llms.txt (S-12).
