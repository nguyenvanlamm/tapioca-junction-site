# Viral evaluation: Tapioca Junction landing page

```
Result: PASS
Virality Score: 63/100 — Needs work
Product: Tapioca Junction, a calm bubble-tea logic puzzle for iPhone (coming soon)
Evaluated: evidence-dir .reports/design-optimizer/evidence (page.html, head.json, screenshots/*) + index.html · codebase tapioca-junction-site (s9-site worktree) and, read-only, tapioca-junction (DESIGN.md, store/en-US/*.txt, lib/store/catalog.dart)
Orchestrated by: design-optimizer (the same run also serves search-optimizer)

PASS: 12/32   PARTIAL: 16/32   FAIL: 4/32
```

Score from `scripts/virality_score.py` over all 32 verdicts. `PASS` above describes evaluation coverage, not product quality.

## Scorecard

### A. Pricing & monetization
```
FAIL  #1  No free plan ············ "House Classics and Fruit Teas: 40 orders — Free"; menus I–II free forever (DESIGN.md §4)
PART  #8  Hard paywall ············ No signup; payment asked only at menu III (Full Menu $3.49). Half the content gated, half free
PART  #12 Popcorn pricing ········· 4 price rows (Free / $3.49 / $1.49 / $0.99) in one list; only one is the real unlock, but they read as 4 options
PART  #16 Pricing impossible to miss  "What it costs" section exists; no header nav at all (header = icon + name), hero shows "40 orders free" but no price
PASS  #27 No subscription ········· Full Menu is non-consumable, "Bought once, yours to restore" (catalog.dart isConsumable)
PASS  #32 Priced above competitors · $3.49 unlock vs the $2.99 unlock common among peers (DESIGN.md P3)   ⚠ check against live store peers
```

### B. Hero & headline
```
PART  #20 Sellable from hero ······ Headline + 33-word sub + static screenshot: clear it is a puzzle, the flip-after-each-pearl rule needs reading   ⚠ stranger 5-second test
PASS  #7  Fifth-grader headline ··· "Set the flippers. Pour the jar. Order up." plain words, no jargon
PART  #18 Emotional headline ······ "Order up." gives a small payoff; mostly instruction, little wow   ⚠ gut read needed
PASS  #17 Memorable headline ······ Three short beats, repeatable, also on the share card   ⚠ next-day recall test
PART  #3  Numbers not adjectives ·· Hero: one number ("40 orders free") beside "calm"; numbers live lower ("eighty orders", "a minute or two")
PART  #24 Human desire ············ Top copy explains the mechanic; the desire (a quiet break, the "it worked" moment) is only implied by "calm" and the facts row   ⚠ judgment
```

### C. Message clarity & focus
```
PASS  #11 Does one thing ·········· One puzzle loop; 4 menus each add one track part; no bolt-ons
PASS  #30 Under 10 words ·········· "A calm logic puzzle at a bubble-tea counter after dark." = 10 words, first line of the sub
PART  #6  One idea per screen ····· "Made to be read at a glance" mixes flavour stamps, the three helps and "Quiet by design"   ⚠ judgment
PART  #22 One CTA ················· Two gradient buttons of equal weight with different jobs: "See how a jar plays out" (#how) and "Contact support"; neither converts
PASS  #28 CTA says what happens ··· "See how a jar plays out" is specific (it lands on text steps, not a moving jar; see fix 2)
```

### D. Proof & differentiation
```
PART  #21 Empathy before selling ·· No problem section; the pain (ads, hearts, timers) is only implied by "No ads · No timers or lives"   ⚠ judgment
PASS  #9  Copy only you could write  "Pshh. The next cup slides up.", "rides the straw up to the return jar", "Taro has a ring, matcha a leaf"   ⚠ judgment
FAIL  #14 Customer language ······· No player voice anywhere (pre-launch)
PART  #26 No weak words ··········· One hedge: "You start with a few and earn more" (Three helps card)
FAIL  #29 Testimonials ············ None: no quotes, ratings or counts (deliberate, see caveats)
FAIL  #31 Compares to competitors · No comparison or "vs" section
PART  #19 Never seen before ······· Familiar sort-puzzle category with one real twist: flippers that flip after every pearl (DESIGN.md §2 row 9)   ⚠ novelty judgment
```

### E. Show, don't tell
```
PASS  #10 Shows product first ····· Order 10 screenshot in the hero (right column at 1280, directly under the CTA at 390)
PART  #25 Try before buying ······· Static screenshot only; nothing moves or can be played on the page
PART  #15 Founder presence ········ Name only, in the footer ("© 2026 Luong Nguyen"); final copy says "We read every message"   ⚠ judgment
```

### F. Visual & shareability
```
PASS  #2  Three colors ············ Dark stage #140C09, cream ink, one purple→red gradient accent on CTAs (approved Night Signal look)
PART  #4  Shareable footer ········ Ends on "The counter opens soon" + "Contact support", then legal links; nothing to pass on   ⚠ judgment
PASS  #5  OG image ················ share-card.jpg 1200×630, og:+twitter:image set; big three-line headline + game shot + "COMING SOON"   ⚠ eyeball at feed size
PASS  #23 Memorable name ·········· "Tapioca Junction": two known words, says what it is   ⚠ spelling of "tapioca" for some
```

### G. Distribution context
```
PART  #13 Rides a wave ············ Bubble tea and sort puzzles are both live trends; the page never says "sort puzzle" or leans on either   ⚠ judgment
```

## Top fixes (impact × ease)

1. Rewrite the hero sub and facts row to sell the payoff with numbers — fixes #24, #3, #18, #20, #16
   Now:    "A calm logic puzzle at a bubble-tea counter after dark. Every pearl flips the flipper it passes, so each jar runs down the route you set before you poured, pearl by pearl." · facts: "No ads · No timers or lives · Plays offline · 40 orders free"
   Change: Keep the headline. Sub: "A calm logic puzzle at a bubble-tea counter after dark. Point the flippers, pour the jar, and watch every pearl land where you sent it. 80 orders, every one checked solvable." Facts: "No ads · No timers or lives · Plays offline · 40 orders free · $3.49 once for the other 40"
   Why:    The hero has to carry the "it worked" feeling and the price; today it carries the rulebook.

2. Show a jar actually pouring — fixes #25, #20, #19, #28
   Now:    Static Order 10 screenshot; "See how a jar plays out" jumps to three text cards.
   Change: Put a 6–10 s muted, looping, autoplaying video (webm + mp4, poster = current game.webp) of one pour inside the same phone frame: flippers ticking left, right, left, right; a cup sealing "Pshh"; "Order up!". Point the hero CTA at it or make the CTA play it. Static files only, Night Signal frame unchanged.
   Why:    The twist (flip after every pearl) is the novelty and is invisible in a still.

3. End on a share, not a support ticket; give the counter a face — fixes #4, #22, #15
   Now:    "The counter opens soon / Questions before then? We read every message. / [Contact support]"
   Change: "The counter opens soon. Know someone who solves puzzles in their head? Send them the counter." Primary button "Share Tapioca Junction" (Web Share API, falls back to copy link; no backend). Demote support to a text link: "Questions? I read every message. Luong, the one person behind the counter." 
   Why:    A coming-soon page with no store link can only spread by being passed on; one solo maker's voice is proof you can show without inventing anything.

4. Name the pain and compare without naming brands — fixes #21, #31, #13
   Now:    Pain only implied by "No ads · No timers or lives".
   Change: Before "The track is the puzzle", add "Sort puzzles, minus the nagging" with a two-column table, "Typical sort puzzle | Tapioca Junction": "Ads between levels | None" · "Hearts that refill by the hour | No lives, restart free" · "Random bounces | Same flips, same result" · "Endless levels marked Hard | 80 orders, each checked solvable".
   Why:    Readers switch when they see what they escape; "sort puzzle" ties the page to a genre people already search and talk about.

5. Split the price list into the game and the extras; add a header nav — fixes #12, #16
   Now:    One list of four rows, Free to $0.99; header has no links.
   Change: Group 1 "The game": "First 40 orders — Free" / "Full Menu, the other 40 — $3.49 once". Group 2 "Optional extras": Apron $1.49, Tip Cup $0.99. Header links: "How it plays · Price · FAQ".
   Why:    One clear decision (free, then $3.49 once) instead of four.

6. Swap the hedge for numbers and give each section one idea — fixes #26, #3, #6
   Now:    "You start with a few and earn more the first time you clear milestone orders." inside "Made to be read at a glance".
   Change: "You start with 3 Undo, 3 Peek and 2 Wide Jar, and earn more on the first clear of every fifth order, up to 9 of each." Move the "Three helps" card into "How it plays"; leave stamps + quiet under "Made to be read at a glance".

Remaining misses not fixable now: #29 testimonials and #14 customer language (no players yet; nothing may be invented). After launch, quote real App Store reviews or TestFlight playtesters who agree to it. #1 / #8 are the deliberate free-40 design.

## What's already working
- #7 / #17 Plain, three-beat headline repeated on the share card.
- #30 A 10-word one-liner as the sub's first sentence.
- #10 The game is on screen above the fold at both widths.
- #11 One loop, one job; every menu adds one track part.
- #9 Specific, crafted copy ("Pshh. The next cup slides up.").
- #27 / #32 One-time $3.49 unlock, no subscription, not the cheapest.
- #28 Specific CTA label; #2 restrained three-colour Night Signal palette.
- #5 1200×630 share card with big text; #23 a name made of known words.

## Caveats
- Low-confidence (judgment/visual), human should eyeball: #5 share card at feed thumbnail size (is the phone shot readable?), #17 next-day recall, #18 emotional pull, #20 stranger's 5-second read of the hero, #24 / #21 desire and pain framing, #6 section rhythm, #9 voice, #15 founder presence, #4 ending, #19 novelty versus live sort puzzles, #13 trend fit, #23 name spelling, #32 price versus current store peers (only DESIGN.md peer notes were read; no store lookup).
- Deliberate constraints scored as written: no store badge, App Store link, waitlist or email capture (game not live, static GitHub Pages, no backend), so the page has no conversion CTA by design and fix 3 uses a share button instead; no invented testimonials, ratings, download counts or awards (#29, #14 fail by design until real players exist); solo developer (fix 3 turns that into the founder voice); the free first 40 orders are the economy design (#1, #8); the approved Night Signal look stays (fixes 2–6 add content inside it, no restyle).
- meta-tags: in this design-optimizer run the manifest assigns it to viral-product-evaluator; head.json is complete (title, description, og:*, twitter:* with 1200×630 image and alt), so no meta fix is listed. For the search-optimizer run: meta-tags: skipped — owned by seo-ai-optimizer. Principle #5 was still scored from head.json.
- Not evaluated: live public URL (evidence captured locally at 127.0.0.1:8747); no outside service contacted.
