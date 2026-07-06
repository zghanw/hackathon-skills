# HACKATHON.md: HackTheWaste 2026 (24h, campus sustainability)

<!-- FICTIONAL WORKED EXAMPLE: output of /hackathon-kickoff, shown so you
     know what the skill produces before you run it. -->

## The one-liner

EcoEats: dining halls post tonight's surplus food in one tap; students within
walking distance get a push alert and claim a free rescue meal before it hits
the bin.

## Urgency hook

Our campus throws away ~340 kg of edible food every day (roughly 900 meals)
while 1 in 4 students report skipping meals to save money; both numbers are
from last semester's sustainability audit, and every day without a fix is
another 900 meals in the dumpster.

## Judging rubric

| Criterion | Weight | Our proof point (what a judge can see working in 30 seconds) |
|---|---|---|
| Impact | 30% | Live claim counter: "meals rescued tonight" ticking up during the demo |
| Technical execution | 25% | Real push notification arriving on a phone on stage, geofenced to 800 m |
| Innovation | 25% | Claim-window algorithm: surplus priced at zero but rationed by walk-time, so food goes to whoever can actually arrive before closing |
| Presentation | 20% | One story, four voices, under 5 minutes (see PITCH.md) |

## Angle decision

| Angle | Impact (30%) | Tech (25%) | Innov (25%) | Present (20%) | Weighted |
|---|---|---|---|---|---|
| **A (chosen): surplus alerts, dining hall → student** | 5 | 4 | 4 | 5 | **4.5** |
| B: AI meal-plan optimizer from dining data | 3 | 4 | 3 | 3 | 3.25 |
| C: campus composting logistics tracker | 4 | 3 | 2 | 3 | 3.05 |

**Why A:** Only angle where the demo moment is a physical event judges can
watch (phone buzzes on stage), and the only one that scores 5 on the
top-weighted criterion.

## Phase plan (back-solved from T+24h submission, 5-min pitch at T+26h)

| Checkpoint | Time | Deliverable | Skill / command | Owner |
|---|---|---|---|---|
| Kickoff | T+0 | This file | `/hackathon-kickoff` | all |
| Spec | T+1.5h | Feature list: post surplus, alert radius, claim + counter | superpowers `brainstorming` | all |
| **Feature Zero** | T+4h | One dining hall hardcoded → push lands on Jun's phone → claim increments counter. Deployed. | | Jun + Maya |
| Core build | T+14h | Real posting form, geofence, claim windows | | Maya (web), Jun (API), Alex (geo + data) |
| QA + polish | T+18h | Bug pass on claim flow; spacing/hierarchy pass | gstack `/qa`, `/design-review`; `ui-ux-pro-max` | Maya + Priya |
| Deck | T+21h | 7 slides + narration script | `beautiful-hackathon-slides` | Priya |
| Pitch script | T+22h | `PITCH.md` | `/pitch-timebox` | Priya |
| Rehearsal ×2 | T+23h | Both runs ≤ 4:45 | | all |
| **Submission** | T+24h | Repo + deck + 60s video | | Jun |

## Team

| Name | Strengths | Owns (build) | Pitch section |
|---|---|---|---|
| Maya | React, fast UI | Web app + claim flow | Live demo |
| Jun | Node/Postgres | API, push, deploy | Team + ask |
| Priya | Design, storytelling | Deck, brand, script | Hook + urgency |
| Alex | Data, maps | Geofence, audit-data stats | Impact + model |

## Scope cuts (running log)

1. Multi-campus support: one campus is the whole demo.
2. Dietary-preference filters: cut first if behind at T+14h.
3. Dining-hall analytics dashboard: a slide mockup is enough for judges.
4. ~~Accounts/login~~ CUT at T+9h: claim via magic link instead, saved ~3h.
