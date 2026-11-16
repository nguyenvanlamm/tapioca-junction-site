# Design Optimization: Tapioca Junction site

Run: design-optimizer 1.1.0 · 2026-11-17T04:40Z · mode: apply (owner opted in at G4)
Evidence: evidence/manifest.json (local capture of the s9-site worktree at 390 px and 1280 px, after the search-optimizer fixes) · AX ownership case: B (no outside scan)
Members: dont-make-me-think √ (COMPLETE, thinking cost MODERATE) · ux-ax-review ~ PARTIAL (performance not tested: no timings, no outside profiler allowed) · website-agent-readiness — skipped (owner did not allow an outside scan) · viral-product-evaluator √ (63/100, Needs work)

## Summary
- Thinking cost (dont-make-me-think): MODERATE, 11 issues (0 red · 5 yellow · 6 green)
- Agent-readiness score: not scanned (owner decision)
- Virality score: 63/100 (12 PASS / 16 PARTIAL / 4 FAIL)
- Findings: 0 P0 · 0 P1 · 11 P2 · 9 P3 (5 cross-member duplicates merged); 15 applied, 5 not applied (reasons below)

## Findings

| ID | Pri | Check | Finding | Evidence | Owner | Also reported by | Fix route / status |
|---|---|---|---|---|---|---|---|
| D-01 | P2 | brand | support.html and privacy.html rendered cream with a system font and no icon, unlike Night Signal | screenshots/support-390-full.png | ux-ax-review F1 | dont-make-me-think DMMT-10 | applied: Night Signal tokens, Sora + DM Mono, icon header, shared footer |
| D-02 | P2 | clarity | No header navigation; prices and support only reachable by scrolling ~5,500 px on mobile | index-390-full.png | dont-make-me-think DMMT-1 | viral #12/#16 | applied: header nav How it plays (≥560 px) · Prices · Support |
| D-03 | P2 | clarity | Hero sub dense, mixed tenses | index.html .hero .sub | dont-make-me-think DMMT-2 | viral fix 1 | applied: "A flipper flips after every pearl it sends, so the route you set decides where each pearl lands." |
| D-04 | P2 | clarity | Full Menu price row ran ~5 lines at 390 px | index.html .prices li:2 | dont-make-me-think DMMT-3 | — | applied: shorter row, keeps the G4 unlock facts |
| D-05 | P2 | conversion | Hero CTA "See how a jar plays out" promised something to watch | index.html hero .btn | ux-ax-review F2 | dont-make-me-think DMMT-4, viral fix 2 | applied: "See how it plays" |
| D-06 | P2 | clarity | support.html long paragraphs; restore steps buried | support.html | dont-make-me-think DMMT-5 | — | applied: How to play as 4 steps, Purchases as bullets, new "Restore a purchase" section |
| D-07 | P2 | virality | Page ended on support only; no way to pass it on | index.html .final | viral-product-evaluator fix 3 (#4, #22) | — | applied: "Send them the counter." + Share button (Web Share API, copy-link fallback, hidden without JS) |
| D-08 | P2 | conversion | Price section did not say the download is free or that prices are USD | index.html #price-h | ux-ax-review F3 | viral fix 5 | applied: "Free to download." lead + USD note |
| D-09 | P2 | llms-txt | Stamp card named 5 of 7 flavours (llms.txt and the game have 7) | index.html #see-h card | ux-ax-review F4 | — | applied: lychee a heart, brown sugar a swirl |
| D-10 | P2 | virality | Helps card hedged ("a few", "milestone orders") | index.html Three helps | viral-product-evaluator fix 6 | — | applied: "3 Undo, 3 Peek and 2 Wide Jar … every fifth order of a menu" (DESIGN.md §4) |
| D-11 | P2 | robots-sitemap | Host-root robots.txt / llms.txt do not list this site | ../search-optimizer/evidence | ux-ax-review F5 | search-optimizer S-12 | not applied here: host-root repo, one chore commit at S9 |
| D-12 | P3 | accessibility | `.facts li::before` "● " read aloud | index.html | ux-ax-review F6 | — | applied: CSS dot |
| D-13 | P3 | accessibility | No skip link, no visible focus style | index.html | design-optimizer intake (ux-ax-review: keyboard not tested) | — | applied: skip link, `:focus-visible` ring in taro on all pages |
| D-14 | P3 | clarity | "Six pearls … left, right, left, right" lists four | index.html #track lead | dont-make-me-think DMMT-6 | — | applied |
| D-15 | P3 | clarity | "Tap it to send them again": unclear "it" | index.html Misses card | dont-make-me-think DMMT-7 | — | applied |
| D-16 | P3 | clarity | "Full Menu" tag used before it is explained as a purchase | index.html .menu .tag | dont-make-me-think DMMT-8 | — | applied: "Full Menu · $3.49" |
| D-17 | P3 | clarity | Heading "Made to be read at a glance" covers helps and quiet-play cards too | index.html #see-h | dont-make-me-think DMMT-9 | — | applied: "Made for calm play" |
| D-18 | P3 | responsive | Footer/404 links ~19–24 px tall | capture measurements | dont-make-me-think DMMT-11 | — | applied: 10 px padding (inline text links unchanged, WCAG 2.5.8 exception) |
| D-19 | P3 | performance | Google Fonts stylesheet may block render (hypothesis, unmeasured) | index.html head | ux-ax-review F7 | — | not applied: measure on the deployed URL first (T1) |
| D-20 | P3 | virality | Static screenshot; a 6–10 s loop of a jar pouring would show the twist | hero | viral-product-evaluator fix 2 | — | not applied: needs recorded gameplay (game-ad-video), out of S9 scope |

Not applied, by design: viral fix 4 (a "typical sort puzzle vs Tapioca Junction" table) — names the reference genre the 4.3 guard steers away from and makes claims about other games; testimonials, player quotes, ratings (#14, #29) — nothing may be invented before launch; waitlist/email capture — no backend, and "coming soon" with no store link is required.

## Skipped (owned elsewhere)
| Check | Skipped by | Owner |
|---|---|---|
| clarity | ux-ax-review | dont-make-me-think |

## Not covered
| Check | Reason |
|---|---|
| agent-readiness-scan | Owner did not allow an outside scan (G4) |

Checks owned by ux-ax-review in case B and found passing or not applicable: structured-data (pass), crawler-access (pass, site-path robots.txt), markdown-pages (n/a for a short pre-launch page), ai-actions (n/a; sharing is D-07). meta-tags (viral-product-evaluator): pass after the search-optimizer fixes.

## Member reports
- reports/dont-make-me-think/usability-review.md
- reports/ux-ax-review/UX_AX_REVIEW.md, ux-ax-findings.json
- reports/viral-product-evaluator/viral-evaluation.md

## Verification after apply
- Headless Chrome at 390 px: no horizontal scroll on index, support, privacy, 404 (scrollWidth = clientWidth = 390); 1280 px also clean.
- Internal links: 52 references in 4 pages + llms.txt/sitemap.xml/robots.txt all resolve (files and #fragments).
- JSON-LD parses on all pages; "marble" appears nowhere in the site.
- Screenshot after: evidence/screenshots/after-index-390.png (screenshots are git-ignored).

## Next step
Deploy (merge to main), then measure load on the live URL (D-19) and add the site to the host-root robots.txt and llms.txt (D-11).
