# SidelineReel — PM Assessment (Ajaia)

**Video:** `<PASTE VIDEO LINK HERE>`
**Prototype:** `<PASTE PROTOTYPE LINK HERE>` (single self-contained HTML file, `sidelinereel-prototype.html`; open in any browser, no install, no network needed)
**Candidate:** Muhammad Izaan · izaanatif@gmail.com
**Optional links:** `<portfolio / LinkedIn / GitHub — or leave blank>`

Prepared for Ajaia ([https://ajaia.ai](https://ajaia.ai)), SidelineReel product team.

---

## TL;DR

- **Build next: Jersey Match Confidence + Coach Review.** Stop wrong-kid clips from reaching a kid's reel or thumbnail. Clips with ambiguous jersey numbers (4 vs 14, 1 vs 11, 12 vs 21) are held back for a quick coach confirmation instead of being guessed.
- **Why:** It is the only problem confirmed by three independent sources: support tickets, the analytics note, and the biggest client's own parents. It hits the product's core job, the personal reel. It is also a hidden cause of the ~30% of reels that are never opened.
- **Not building next:** livestreaming, and more Reel Editor controls. Livestreaming is outside the core job and too big to deliver before Ridgeline's signups. Parents ask for editing in the survey but don't use the editor.
- **For Ridgeline:** a concrete, honest answer. Their parent's 14-vs-4 complaint gets fixed before signups, and they get a Ridgeline accuracy report to take to the board. Livestreaming goes into scoped discovery, not a roadmap promise.

---

## Task 1 — The roadmap call

### 1.1 What the signal actually says

| # | Signal | What it looks like | What it actually tells us | Weight |
|---|---|---|---|---|
| M1 | Carla (Ridgeline) wants livestreaming | Loud, urgent, biggest account | Her own words: *highlight reels* are why half her parents renewed. Livestream is a board ask for grandparents and scouts, not a reported failure of the product. | High commercial risk, low evidence it is the right fix |
| M2 | Survey: 58% want more editing | Clear user demand | Stated vs. revealed preference. 6% of parents opened the Editor and <1% of those finished an edit. Parents use the **Share** button on 90% of auto-recaps. They want reels that are right and easy to share, not a tool to fix them by hand. | Low (stated only, self-selected sample) |
| M3 | 3 of 5 tickets: wrong kid in reel | Just a few tickets | Three different clubs and three sports (soccer, lacrosse, baseball). Same pattern every time: visually similar numbers (14→4, 1→11, swapped digits). One is a **Ridgeline** parent. The bug sits in the core job. | **Highest** |
| M3 | Icon, watermark | Minor | Real but cosmetic. No retention impact shown. | Low |
| M4 | Sales: "any version of livestream we can commit to?" | Pressure for a commitment | $180k is real money. But the request is for *a commitment*, not evidence that livestreaming retains the account. Committing to a "lite" livestream in 6 weeks creates a second, bigger renewal risk if we miss. | Commercial context, not product evidence |
| M5 | Reel Share Rate 92% | Looks healthy | Counted only over **opened** reels. ~30% are never opened, so the share rate over *generated* reels is ≈ 0.70 × 0.92 ≈ **64%**. The analytics team names two causes of unopened reels: late-night notifications and **wrong-kid thumbnails on similar jersey numbers**. | High: it exposes the cost of M3 |

**The pattern:** M3 and M5 point at the same root cause from two different directions (anecdote and data). M1 indirectly confirms it: Ridgeline's renewal rests on reels, and Ridgeline's reels have this bug. The loudest asks (M1, M4) and the most popular stated ask (M2) are not what the evidence supports.

### 1.2 Ranked roadmap

| Rank | Item | Evidence | Expected impact | Effort (rough) |
|---|---|---|---|---|
| **1** | **Jersey Match Confidence + Coach Review** (hold ambiguous clips for a 1-tap coach confirm; only confident clips drive thumbnails; parent "Not my kid" flag) | M3 (3 clubs), M5 analytics note, M1 (Ridgeline parent affected) | Fewer wrong-kid clips, more reels opened, protects the reel value Ridgeline renews on | Medium: uses the existing tagging output plus a small review UI |
| **2** | **Fix reel notification timing** (send in the family's local daytime window, not when processing finishes) | M5 analytics note (late-night delivery is a named cause of unopened reels) | Opens up, cheaply. Stacks with #1 | Small |
| **3** | **Fix the health metric** (replace "Share Rate over opened reels" with *Reel Open Rate* + *Share Rate over generated reels* + *Wrong-kid flag rate*) | M5 | Stops the team steering by a flattering number. Needed to measure #1 and #2 | Small (analytics) |
| **4** | **Livestreaming: discovery only** (2-week scoped interviews with the Ridgeline board: who watches live, why, what "scouts" actually need; test cheaper alternatives such as same-day recap or full-game replay for rostered families) | M1, M4 | Turns a vague ask into a sized decision before any build commitment | Small (PM + research time) |
| 5 | Watermark missing on camera-roll save | M3 (1 coach, "not urgent") | Brand polish | Small, backlog / bug queue |
| 6 | App icon for multi-sport leagues | M3 (1 parent) | Cosmetic | Backlog |

### 1.3 What I would NOT build next, and why

**1. Livestreaming for Ridgeline: not next.**
- **Outside the core job.** SidelineReel's job is *find each kid's moments → personal reel → weekly recap*. Livestreaming is a different product: real-time infrastructure, latency, per-field camera reliability, bandwidth at youth fields, and moderation.
- **Safeguarding risk.** Streaming minors live to the public (and to "college scouts") needs consent, access-control and child-safety work that we don't have today. Getting that wrong costs far more than one account.
- **Six weeks is not enough to ship it well.** Committing to "some version" just to win the renewal swaps a known risk (Carla shops around) for a worse one (we promise, miss or ship something poor, and lose credibility with our biggest client).
- **Her own evidence points elsewhere.** Carla says reels drove half her renewals, and a Ridgeline parent just reported a wrong-kid reel. The most effective thing we can do for the renewal is make sure the reels her parents get are right.

**What we tell Carla (concrete, not "we hear you"):** Jamal and I take this to her, and I'd join the call.
> "Livestreaming is not on the roadmap for this season and we won't promise a version we can't stand behind. Here's what we will commit to before your signups open: (1) the jersey mix-up your parents reported, like the #14 / #4 clip, fixed for Ridgeline, with a before/after accuracy report you can show your board; (2) reels delivered at times families actually open them; (3) a 2-week discovery with you and two board members on what live viewing needs to do for grandparents and scouts, with a written yes/no/when by [date]."

**2. More Reel Editor controls (trim, music): not next.**
58% *say* they want it, but only 6% open the Editor and fewer than 1% of those finish an edit. Parents don't want to edit. They want the auto-generated reel to be right, and they share the auto-recap 90% of the time. Better editing would also put the work of fixing our tagging mistakes on parents. Before investing, I'd look at why Editor sessions are abandoned, and I wouldn't build more controls.

**3. App icon and watermark: not next, but logged.** They are valid and cheap, so they go in the bug and polish queue, not the roadmap.

### 1.4 Anticipated pushback (and why I'd hold the call)

- **"We'll lose $180k."** Possible, and I take it seriously. But a livestream promise we can't keep loses it later *and* damages the relationship. Carla gets a dated, concrete answer and a fix to the problem her parents actually reported. If discovery shows live viewing is a real retention driver across many clubs, not just one board, it earns a place on the roadmap with proper sizing.
- **"Parents told us they want editing."** They told us in a survey. Their behaviour tells us otherwise, and behaviour from all accounts outweighs a 210-person self-selected survey.
- **"Share rate is 92%, reels are fine."** That's 92% of *opened* reels. Across everything we generate it is about 64%, and wrong-kid thumbnails are one named reason reels go unopened.
- **"Only 3 tickets."** They come from three clubs and three sports with an identical failure pattern, and the analytics team points to the same cause. Most parents who get a wrong reel won't file a ticket. They just don't open the next one.

---

## Task 2 — Spec: Jersey Match Confidence + Coach Review

### 2.1 Problem
Roster tagging maps a jersey number seen in footage to a roster name. When numbers are visually similar (one is contained in the other, like 4/14 or 1/11, or the digits are swapped, like 12/21), the tagger sometimes picks the wrong kid. That wrong clip lands in another kid's personal reel and can become the reel's **thumbnail**. Parents notice immediately, feel let down, and stop opening reels.

### 2.2 Outcome (what success means)
| Metric | Baseline | Target (8 weeks post-launch) |
|---|---|---|
| Wrong-kid flag rate (parent "Not my kid" flags per 1,000 clips delivered) | Establish in week 1 (flag ships first) | −70% vs. baseline |
| Reel Open Rate (opened / generated) | ~70% | ≥ 78% (with #2 timing fix contributing) |
| Share Rate over **generated** reels | ~64% | ≥ 70% |
| Coach review completion (held clips resolved before send) | n/a | ≥ 80% |
| Highlight parity: avg clips per kid, confusable-number kids vs. others | unknown | within 10% (we must not "fix" accuracy by starving some kids of highlights) |

Ridgeline-specific: before/after accuracy report delivered to Carla before signups open.

### 2.3 How it works
1. **Confidence on every tag.** The tagging step already produces a match. It must now also return a **confidence score (0–1)** and the **runner-up roster match**, if any.
2. **Confusable pairs from the roster.** When a roster is created or edited, the system computes *confusable pairs*: two roster numbers where (a) one number's digits are contained in the other (4/14, 1/11, 7/17, 2/22), or (b) the two-digit numbers are digit swaps (12/21, 36/63). (Config list, extendable, e.g. 6/8 or 3/8 if data shows it.)
3. **Routing rule** for each tagged clip:
   - confidence ≥ **0.90** and the matched number **is not** in a confusable pair → **auto-approve**
   - confidence ≥ **0.97** and in a confusable pair → **auto-approve**
   - anything else → **Held for coach review**
   - Thresholds are server-side config per sport, not hard-coded.
4. **Held clips never auto-publish.** They are excluded from reels and from thumbnail candidates until a coach confirms. At the scheduled send time, unresolved held clips are **left out**. We always prefer a missing clip to a wrong-kid clip.
5. **Thumbnails come only from auto-approved or coach-confirmed clips**, and the clip must contain the reel owner with confidence ≥ 0.95.
6. **Coach Review queue** (coach app): a list of held clips grouped by game. Each item shows a zoomed still of the jersey area, a 3-second clip loop, the suggested kid, the confusable alternative(s), and four actions: **Confirm [suggested]**, **It's [alternative]**, **Pick someone else** (roster list), **Not our player / Remove**. Target is under 5 seconds per decision.
7. **Coach nudge:** one push or email 24 h before recap send if held clips exist ("3 clips need a quick check before Saturday's reels"). No more than 1 nudge per week.
8. **Parent "Not my kid" flag** on every clip in a personal reel. It instantly hides that clip from *that* reel for *that* family, sends it to the coach queue, and logs a label.
9. **Every coach decision and parent flag is stored as a labelled example** (clip id, predicted, final, source) for the ML team's future retraining. Retraining itself is out of scope.

### 2.4 Scope
**In scope**
- Confidence + runner-up output exposed from the tagging step
- Confusable-pair computation on roster save
- Routing rule + config thresholds
- Hold/exclude logic for reels and thumbnails
- Coach Review queue (list + review screen + 4 actions)
- Weekly coach nudge (max 1)
- Parent "Not my kid" flag + instant hide
- Label logging
- New metrics on the Product Health dashboard: Open Rate, Share Rate over generated, Wrong-kid flag rate, Review completion, Highlight parity

**Out of scope (explicitly)**
- **Face recognition or any biometric identification of children.** Not doing it, for privacy and safeguarding reasons
- Retraining or replacing the tagging model (we only collect labels)
- Livestreaming, Reel Editor changes, watermark fix, app icon
- Notification send-time change (roadmap #2, separate ticket)
- Letting parents reassign a clip to another kid (only coaches reassign; parents can only flag)
- Re-sending already-delivered recaps from past weeks

### 2.5 Human in the loop
| Decision | Who | Why |
|---|---|---|
| Ambiguous clip: which kid is this? | **Coach** confirms or reassigns | Coaches know their players. The system never guesses on an ambiguous clip. |
| Clip shown to a family that isn't their kid | **Parent** flags; system hides instantly; coach decides final | Parents are the best detectors. Hiding is safe and reassigning needs the coach. |
| Thresholds and confusable rules | **PM + ML lead** review weekly for the first 4 weeks using flag-rate and parity data | Calibration is a judgement call. It is not auto-tuned. |
| Nothing ambiguous is ever auto-sent | System rule | Fail closed |

### 2.6 Acceptance criteria (testable)
1. **Given** a roster containing #4 and #14, **when** the roster is saved, **then** the pair (4, 14) is stored as confusable. Same for (1, 11) and (12, 21). (13, 31) is only stored if both exist on the roster.
2. **Given** a clip tagged #14 with confidence 0.93 on a roster that also has #4, **then** the clip status is *Held* and it does not appear in any personal reel, team recap or thumbnail.
3. **Given** a clip tagged #9 with confidence 0.93 and no confusable pair for 9, **then** the clip is *Auto-approved*.
4. **Given** a clip tagged #14 at confidence 0.98 with #4 on the roster, **then** it is *Auto-approved*.
5. **Given** a held clip, **when** the coach taps *Confirm*, **then** it is added to the suggested kid's reel within 5 minutes and logged as label `source=coach, final=predicted`.
6. **Given** a held clip, **when** the coach taps *It's #4*, **then** it is added to #4's reel, not #14's, and logged `final≠predicted`.
7. **Given** held clips are still unresolved at recap send time, **then** the recap sends on schedule without those clips, and the clips stay in the queue marked *Missed send*.
8. **Given** a parent taps *Not my kid* on a clip, **then** that clip disappears from that reel on their next screen refresh (≤ 5 s), a queue item is created for the coach, and the reel thumbnail is recalculated if the flagged clip was the thumbnail.
9. **The reel thumbnail** is never a Held clip, and never a clip with owner confidence < 0.95.
10. **The coach nudge** is sent at most once per team per week, and only if at least 1 held clip exists 24 h before send.
11. **Changing thresholds** in config takes effect for newly tagged clips without a deploy.
12. **The dashboard** shows Open Rate, Share Rate (generated), Wrong-kid flag rate, Review completion, Highlight parity, each with its definition shown under the number.
13. **No new biometric data** is collected or stored (privacy review sign-off).

### 2.7 Top two ways this fails after launch, and what catches each

**Failure 1: Coaches don't do the reviews, so reels get thinner and kids with confusable numbers lose highlights.**
We've moved the error from "wrong kid" to "missing kid". That's better, but if #4 and #14 rarely get clips, those families are still let down.
- **Catches it:** Review completion rate (< 80% alerts), **Highlight parity** metric (confusable-number kids vs. others, alert at > 10% gap), held-clips-per-team-per-week (alert if > 10).
- **Response:** Tune thresholds, batch reviews into a single 1-minute weekly session, and let an assistant coach or team manager review.

**Failure 2: The model is *confidently* wrong, so wrong-kid clips still pass auto-approve.**
Occlusion or motion blur can make #14 look like a clean #4 at 0.98 confidence. The routing rule never sees an ambiguity.
- **Catches it:** **Wrong-kid flag rate** per 1,000 clips, split by auto-approved vs. coach-confirmed, plus a **weekly audit**: a human checks a random 50 auto-approved clips from confusable pairs.
- **Response:** Raise the confusable-pair threshold, add a "held if confusable alternative appears in the same frame" rule, and feed flagged clips to the ML team as priority labels.

*(Third risk to watch: the parent "Not my kid" flag gets misused, e.g. parents flag clips they just don't like. Track flags that coaches overturn. Flags only hide a clip for that family, so misuse can't hurt other kids' reels.)*

### 2.8 Rollout
1. Week 0: ship the parent flag + new metrics first, to establish the baseline.
2. Week 1: confidence routing + coach queue to **Ridgeline + Brightwater + Cobblestone** (the reporting clubs) behind a flag.
3. Week 3: review the metrics against targets, then all accounts.
4. Before Ridgeline signups: Ridgeline accuracy report to Carla.

---

## Task 3 — Prototype

**File:** `sidelinereel-prototype.html` (runs offline, single file, click-through).
**Link:** `<PASTE PROTOTYPE LINK HERE>`

The core flow, three screens:
1. **Tagging results → routing.** One game's tagged clips with confidence, confusable-pair detection computed live from the roster, and Auto-approved vs. Held status. A threshold slider shows how routing changes.
2. **Coach Review.** Work through held clips: zoomed jersey still, suggested kid vs. confusable alternative, Confirm / It's #X / Pick someone else / Remove. Decisions update reels live.
3. **Parent reel.** A family's personal reel. Held clips are never shown, the thumbnail is chosen only from confident clips, and a "Not my kid" flag instantly hides a clip and sends it back to the coach queue.
- A metrics strip shows the old 92% Share Rate next to the honest Share Rate over generated reels.

All data is simulated. Player names are fictional.

---

## Task 4 — AI Workflow Note

I used AI (Claude) to cross-read all five materials quickly, compute the true share-rate math (0.70 × 0.92 ≈ 64%), draft the spec structure and acceptance criteria, and write the prototype code. I kept the decisions human: the ranking, the call not to commit to livestreaming, the wording of what we tell Carla, the "fail closed, missing clip beats wrong clip" principle, and the success thresholds. **What I caught and changed:** the AI's first prototype draft held 8 of 12 demo clips for coach review. That would make the coach queue unusable, which is exactly my Failure Mode 1, so I had the confidences and thresholds re-tuned to a realistic review load. Its sliders also re-rendered on every drag, which broke the demo. I also deliberately kept face recognition out of scope even though it is the "obvious" AI fix for identity, because biometric identification of minors is a safeguarding risk. And I checked the AI's confusable-pair rule by hand against the three tickets (14→4, 1→11, swapped digits) to make sure it covers each case.

---

*SidelineReel is part of the Ajaia suite — [https://ajaia.ai](https://ajaia.ai).*
