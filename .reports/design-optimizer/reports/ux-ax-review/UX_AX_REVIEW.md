# UX / AX Review: Tapioca Junction landing site

## Executive Summary

**Outcome: PARTIAL** (performance is not-tested: no timings in the bundle and no profiler allowed). 7 findings (6 observed, 1 hypothesis), 9 plan tasks. No critical or high findings.

Strengths: the index states "Coming soon to iPhone" with no store badge or link; prices are explicit; support is reachable from a closing CTA and the footer; all computed text contrast passes (lowest 5.26:1); no horizontal overflow at 390 px; JSON-LD, sitemap, canonicals, site robots.txt and llms.txt from the search pass are sound and invent nothing.

Top priorities:
1. T3 (P2): apply the approved Night Signal style to support and privacy (F1).
2. T5 (P2): list the site in host-root robots.txt and llms.txt (F5).
3. T1 (P2): measure load on the deployed URL before any font work (F7).

## Scope and Evidence

- Orchestrated by: design-optimizer. Mode: evidence-only (bundle captured 2026-11-17T04:40:00Z; host-root files captured 04:15Z). Lab/capture evidence, not field data.
- Audience: adults 25-50 who play calm logic puzzles on iPhone. Goal: explain the game and prices before launch; route questions to support.
- Sample: index.html (entry + prices), support.html (goal destination), privacy.html; 404.html checked as a bonus surface.
- Skipped: `clarity` (owned by dont-make-me-think). No other skip ids.
- Tools: file reads, screenshot viewing (390x844, 1280x800, full-page), Python contrast computation, grep of the game source. No browser interaction, keyboard or screen-reader run, profiler or external validator (outside services forbidden).
- Output dir sits inside a git worktree; per the orchestrator's instruction no git sync/stash was run. Target snapshot: SHA-256 of 13 site files taken before writing.

| ID | Source | Observation |
|---|---|---|
| E1 | evidence/manifest.json | No overflow at 390 on 4 pages; support/privacy use system-ui; no timings |
| E2 | index.html:42-44,68,121-124,165-182 | Google Fonts stylesheet; `::before "● "` bullets; CTA "See how a jar plays out" → #how text steps; 5 flavours named; USD prices, no base-price note |
| E3 | support.html / privacy.html:24-26 | Light default palette, dark only via media query, system-ui, no icon header |
| E4 | screenshots/index-390*, index-1280* | Night Signal renders; heart-stamped cup visible in hero |
| E5 | screenshots/support-390-full, privacy-390-full | Cream, system-ui, purple links, no icon |
| E6 | 404.html + 404-390.png | Styled, noindex; icon broken only because local server roots site at / |
| E7 | robots.txt, sitemap.xml | Allow-all intent; 3 URLs match self canonicals |
| E8 | search-optimizer/evidence robots.txt, llms.txt | Host root lists 32 sitemaps, not this one; no llms entry |
| E9 | llms.txt | Well-formed; 7 flavours, helps 3/3/2, free to download |
| E10 | JSON-LD (index, support, privacy) | VideoGame+MobileApplication, Upcoming, no offers; FAQ matches visible |
| E11 | Python WCAG contrast | All pairs 5.26-12.31:1 |
| E12 | tapioca-junction/lib/game/flavor.dart | Lychee and brown sugar exist in game |
| E13 | file sizes | webp hero 28.6 KB, png fallback 276 KB, no JS |

## Human UX

| Aspect | Status | Rationale | Refs |
|---|---|---|---|
| clarity | not-tested | skipped — owned by dont-make-me-think | — |
| brand | issues | Index/404 hold Night Signal; support/privacy look like a different site | E3 E4 E5 E6, F1 |
| responsive | pass | No overflow at 390 on all pages; good stack at 390 and 1280. Untested: 320, 768-820, zoom, landscape | E1 E4 E5 |
| accessibility | issues | Contrast passes; semantics sound in source; decorative bullets exposed. Keyboard/SR not run | E2 E11, F6 |
| performance | not-tested | No timings; small payload; font stylesheet is a hypothesis | E2 E13, F7 |
| conversion | issues | Coming soon honest, prices listed, support reachable; CTA label and price context gaps | E2 E4, F2 F3 F1 |

## AI/Search AX

| Aspect | Status | Rationale | Refs |
|---|---|---|---|
| robots-sitemap | issues | Sitemap/canonicals/noindex consistent; host-root robots.txt (the one crawlers read) lacks this sitemap | E7 E8, F5 |
| structured-data | pass | Valid, fitting types, Upcoming, no invented offers/ratings, FAQ matches page. Eligibility not assessed | E10 |
| markdown-pages | not-applicable | Optional; three short pages plus llms.txt summary; .md twins would duplicate | E9 |
| llms-txt | issues | Site file good and matches game; page lags it on flavours; root has no entry. llms.txt is a proposal, adoption unproven | E9 E12 E2 E8, F4 F5 |
| crawler-access | pass | Consistent allow intent incl. training (owner choice, kept); content in static HTML. Deployed headers/bot logs not tested | E7 E8 E13 |
| ai-actions | not-applicable | No content or task output to copy or hand to an AI; sharing is the virality member's | — |

## Prioritized Findings

| ID | Aspect | Kind | Sev / Conf | Problem | Recommendation | Evidence |
|---|---|---|---|---|---|---|
| F1 | brand (+conversion) | observed | medium / high | Support and privacy render cream, system-ui, no icon: the support CTA leaves the approved Night Signal look | Use index tokens (stage #140C09, ink, links #E0CEF8), color-scheme dark, Sora/DM Mono, icon + name header linking home; content unchanged | E3 E5 |
| F2 | conversion | observed | low / high | Hero CTA "See how a jar plays out" lands on three text steps | Relabel "See how it plays" | E2 E4 |
| F3 | conversion | observed | low / medium | Price block omits free download and USD/local-price note | Lead: "Free to download. ... Prices in US dollars; the App Store shows your local price." | E2 E9 |
| F4 | llms-txt | observed | low / high | Index names 5 flavour stamps; llms.txt, game and hero shot have 7 | Add "lychee a heart, brown sugar a swirl" | E2 E9 E12 E4 |
| F5 | robots-sitemap (+llms-txt) | observed | low / high | Host-root robots.txt and llms.txt lack this site | Add Sitemap line and llms bullet in nguyenvanlamm.github.io | E8 |
| F6 | accessibility | observed | low / medium | `.facts li::before` "● " read aloud (WCAG 1.3.1) | `content: "● " / ""` or a CSS dot | E2 |
| F7 | performance | hypothesis | low / low | Render-blocking Google Fonts stylesheet may delay first render; unmeasured | Measure first; then self-host woff2 with preload if needed | E2 E13 |

No ratings, downloads, awards, testimonials or store links are proposed.

## Improvement Plan

| ID | Phase | Pri | Findings | Task | Owner | Effort | Deps | Impact | Acceptance check |
|---|---|---|---|---|---|---|---|---|---|
| T1 | 0 | P2 | F7 | Lab-measure index on the deployed URL | dev | XS | — | Data for F7 | LCP, CLS, font timing at 390 px recorded with tool/date, repeated once |
| T2 | 0 | P2 | — | Verify deployed 404 and asset paths | dev | XS | — | Confirms local-only icon break | Missing URL returns 404 with icon and all links resolving |
| T3 | 1 | P2 | F1 | Night Signal on support and privacy | design/dev | S | — | Same-site feel on the goal page | 390 px light+dark screenshots show dark stage, Sora, icon header; contrast >= 4.5:1 |
| T4 | 1 | P3 | F6 | Hide decorative bullets from AT | dev | XS | — | Cleaner SR reading | VoiceOver reads facts without "black circle"; dots still visible |
| T5 | 2 | P2 | F5 | List site in host-root robots.txt and llms.txt | dev | XS | — | Sitemap found via the robots file crawlers read | Root files contain the entries; linked URLs return 200 |
| T6 | 2 | P3 | F4 | Name all seven flavour stamps | content | XS | — | Page/llms/game agree | Card lists the same 7 as llms.txt |
| T7 | 2 | P3 | F3 | Free-download and currency note | content | XS | — | Fewer price questions | Note present; no store link or badge |
| T8 | 3 | P3 | F2 | Relabel hero CTA | content | XS | — | Label matches destination | Reads "See how it plays"; still reaches #how by mouse and keyboard |
| T9 | 3 | P3 | F7 | Self-host fonts only if T1 shows delay | dev | S | T1 | Faster first render, no third party | Same T1 test improves; no Google Fonts requests |

## Limitations and Next Step

- Not-tested: clarity (skipped), performance (no timings). Untested subchecks: 320 px and tablet widths, zoom/reflow, keyboard and screen reader, dark-scheme render of support/privacy, deployed headers and verified crawler access, rich-result eligibility.
- No WCAG certification, indexing, AI-citation or conversion uplift is claimed. llms.txt is a proposal; provider use is unproven.
- Artifacts: `/home/lam/Documents/projects/tapioca-junction-site/.claude/worktrees/s9-site/.reports/design-optimizer/reports/ux-ax-review/UX_AX_REVIEW.md` and `.../ux-ax-review/ux-ax-findings.json`.

Would you like me to implement any of these fixes? Choose the finding/task IDs and scope.
