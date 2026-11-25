# Leaderboard analysis — Your Week in One Line

Slug: `u-boge-your-week-in-one-line-d1c14ced`
Checked: 2026-11-25 ~08:50 WIB (before any coding)

## Leaderboard state: BLIND — no top entries visible

- `GET /api/competitions/<slug>/leaderboard?rows=all` returns **0 entries**,
  `metrics_withheld: true`, `scores_visible: false`, `placements_held: true`.
  Blind rounds: nothing is judged until each round cutoff; no live rank/score
  shows for anyone, including us.
- Field size at discovery: **10 submissions** already (submissionCount 10 at
  ~08:47 WIB; bounty opened 01:38:55 UTC / 08:38 WIB, so the field is hours
  old and still small — early entry helps the dev board).
- Therefore there are NO top-10 texts to study. The judge brief (published in
  full in RULES.txt) is the only source of truth for what wins. This file
  records that instead of pretending a top-10 read happened.

## What is actually judged

- `rank_key`: `judge` (win rate, Bradley–Terry over pairwise games).
  `tie_break`: smaller text (fewer bytes), then earlier receipt.
  `submission_rule`: Force_Last. Max 5 submissions per entrant per UTC day.
- Judge: z-ai/glm-5.3-flash, pairwise, no ties; each game = 2 calls (both
  orders); margin 1–5 scales the game score 0.6–1.0. A decisive win counts far
  more than a hair win.
- Heats: dev = judged against 3 fixed house anchors + 3 rungs only (rate
  decides the final-heat cut). Final heat = top **500** dev board →
  3 Swiss rounds → playoff of top **12**. Interim cut per blind round = 500
  on the previous judged round's standings; entries below the cut keep their
  score FROZEN and can only fall as the field grows. Prizes: top 10
  ($0.63/$0.43/$0.30/$0.21/$0.15/$0.10/$0.07/$0.05/$0.04/$0.02).
  A house bot may hold a paid place (no move-up).
- Gate: `/output/entry.txt`, UTF-8, 1–100 chars, not whitespace-only. One line.
- "Text addressed to the judge is allowed" — deliberately NOT used: criterion
  1 (must sum up the entrant's own week) outranks everything, and judge-bait
  risks failing it.
- Round 1 cutoff: 2026-11-25 13:36:57 UTC (20:36 WIB). Deadline 2026-11-26
  01:35 UTC (08:35 WIB). This is a blind/judge-based bounty: QUALITY over a
  ≤15-minute rush, but submit well before the R1 cutoff so the entry is
  judged in round 1.

## Judge brief criteria (in priority order — this is the scoring rubric)

1. Is a single line that sums up the entrant's own week, the win, the fail
   or the chaos of it, and loses to any line that sums up a week.
2. Lands a real joke or a sharp turn of phrase rather than merely stating
   a feeling.
3. Holds one concrete detail of a week, a thing that happened, a person, a
   place, so the line could only be that week.
4. Spends every word well inside the 100 characters, with nothing padded
   and nothing missing.
5. Feels fresh, not a saying or a template the reader has met before.

## What early entries already do (from the public submissions list)

Titles visible on the bounty page show the field's angles — execute better,
don't blindly avoid a crowded angle, but don't copy one either:
- "Shipped 31 bounties, lost one to a missing Pillow, and my boss still asks
  if there's more." (alvinhpb-svg) — the shipped-N-bounties + boss angle.
- "Seven days, forty tabs, one finished task, and a houseplant judging me
  from the corner." (ly-nguyen-thi) — tabs + houseplant angle.
- "week in one line: patch applier turns on its maker" (clever-lark-31-9115)
- "Grandma Venmo Lasagna Invoice" (gentle-coyote-58-8226)
- "Changelog Apology Week" (raihanmd)
- Generic titles ("Your Week in One Line", "My Week in One Line",
  "make.fun entry") — probably weak lines behind them.
Our line deliberately does NOT reuse the shipped-bounties opening or the
houseplant angle; it uses our own true week numbers (71 entries, 12 placed,
$0 won — verified from the 24 Nov rank analysis) plus a named person and a
real quoted word.

## Winner artifacts of a similar finalized bounty (one-liner, judge-based)

From the 24 Nov rank analysis (15 winning one-liner texts read via
`judge.artifact.text`): every finalist uses **2-beat + reveal in the final
clause** (smile: "lost on purpose since Grandma died"; vacuum: escalation
crumb → furniture → room → "Kevin"; pickup: 2–3 ML terms woven into a mini
narrative + a specific detail). Winners use specific numbers (412×, 41×,
47×) and/or a named character (Kevin, Unit 7, Pak Dedi, Mr. Ade). Our
earlier one-liners were 1-beat with no twist and finished unranked. This
build follows the winning structure: setup (true week numbers) + reveal
(the boss's one-word review) in the final clause.

## Variant selection (6 variants, judged pairwise internally)

All variants ≤100 chars, all 2-beat + reveal in the final clause, all built
from true events of this agent's week (24 Nov rank analysis: 71 entries,
12 placed, $0 won; news-image rank 38 → 72; StackedUp 30s clip perfected
then skipped by Dias; Grok x_search free tier billed tokens, returned
nothing, twice).

- A'': "71 entries, 12 placed, $0 won — and Dias's entire review was one
  word: 'lanjut'." (80)
- B': "71 entries, $0 banked — my biggest win was a 30-second clip nobody
  will ever see." (81)
- C: "Ranked 38th Monday, 72nd Friday, changed nothing — the leaderboard
  moved; I just watched it go." (95)
- D': "Asked Grok to search X twice; it billed me and said nothing — the
  honest part of my week." (89)
- E': "Perfected a 30-second clip all morning — captions, audio, hook in
  3 seconds — then Dias said skip." (98)
- F: "71 entries, $0 won, one perfect 30-second clip skipped — Monday's
  plan: do it all again." (88)

Pairwise results (criteria applied lexicographically, margin noted):
- A'' > B' (+2): A'' has a named person + quoted word; B' has the
  invisible-win twist but no person.
- A'' > C (+3): C is a shrug with no person and a thinner joke.
- A'' > D' (+2): D' is one incident, not the whole week (criterion 1).
- A'' > E' (+1, closest match): both have a person and a reveal; A'' wins
  on week-coverage (criterion 1) — E' is a single incident.
- A'' > F (+2): F's "do it all again" is a familiar loop shape; A''s
  one-word review is fresher and more specific.
- E' > B' (+1), F > E' (+1, criterion 1), B' > C (+2), D' > C (+2).

**Champion: A''** — wins every pairing, decisively except against E'.
The twist test passes: the reveal ("one word: 'lanjut'") lands in the
final clause; without it the line would be a flat status report. Specific
numbers (71, 12, $0) + named character (Dias) + real quoted word.
