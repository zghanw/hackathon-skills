---
name: pitch-timebox
description: Given a pitch time limit, a team roster, and (optionally) an existing deck or narration script, produce a per-section timing table, speaker assignments, a word-count-budgeted script, and a rehearsal checklist. Use once the deck/story exists and the team needs to decide who says what and when.
---

# Pitch Timebox

Distributes a fixed pitch time limit across sections and named teammates, so
nobody freestyles on stage and nobody fights over who talks when.

## Prerequisites

None required — this works from just a time limit and a roster. It gets
better with more material to slice: `HACKATHON.md` (from
`/hackathon-kickoff`) for rubric weights and the urgency hook, and a deck or
narration script (from `beautiful-hackathon-slides` or the `pptx` skill) to
cut into sections instead of drafting new copy from scratch.

## Inputs to gather

1. Total pitch time limit (e.g. "5 min + 2 min Q&A") — ask if unknown, don't
   assume a default.
2. Team roster: names, and optionally who's strongest at what (demo-driving,
   storytelling, technical Q&A).
3. Whatever narrative material already exists: `HACKATHON.md` (angle +
   urgency hook), a deck, or a narration script from `beautiful-hackathon-slides`.
   Reuse and slice this material — do not draft a new script from nothing if
   one already exists.
4. The rubric weights from `HACKATHON.md`, if present, to decide which
   sections get more airtime (a criterion worth 40% of the score deserves
   more seconds than one worth 10%).

## Workflow

1. **Compute the word budget.** ~130–150 spoken words per minute, minus a
   ~10% buffer for pauses, demo dead air, and applause. A 5-minute slot is
   roughly 550–650 usable words, not 750.
2. **Split sections by rubric weight**, defaulting to this shape if weights
   are flat or unknown:
   - Hook + problem urgency — 15%
   - Solution + live demo — 45% (protect this; judges fund what they see work)
   - Impact / why now — 20%
   - Team + close/ask — 10%
   - Buffer for stumbles / questions — 10%
3. **Assign speakers to contiguous blocks.** One person per block minimum;
   never split a single sentence across two speakers. Route the demo block
   to whoever is most fluent driving the live app, not just whoever coded it.
   Every speaker gets an explicit last line that cues the next person by name
   or topic — no dead air at handoffs.
4. **Write the timed script.** Output a table: `start–end | speaker | section
   | word budget | verbatim or bullet script | handoff line`. Mark the live
   demo block with a fallback instruction (screen-record backup if the live
   demo fails).
5. **Draft Q&A prep.** One likely judge question per rubric criterion, with a
   one-line answer and who answers it (usually the person who owns that part
   of the build). Pull candidate questions from
   `${CLAUDE_PLUGIN_ROOT}/references/judge-questions.md` — pick the ones this
   team's weakest criterion invites, not just the easy ones.
6. **Rehearsal checklist.** Run it with a stopwatch at least twice; if any
   run goes over by more than 10%, cut content — don't speed up delivery.
   Confirm every handoff line lands, confirm the demo fallback plays, confirm
   whoever answers Q&A actually knows that answer cold.

## Output

Fill in `${CLAUDE_PLUGIN_ROOT}/templates/PITCH.md` and write it as `PITCH.md`
in the repo root — the timing table, speaker assignments, demo fallback, Q&A
prep sheet, and rehearsal checklist — so the team can print or read it one
hour before going on stage.

A fully worked example (fictional 24h hackathon, 4 speakers, 5-minute limit):
`${CLAUDE_PLUGIN_ROOT}/examples/ecoeats-24h/PITCH.md`. Match its level of
specificity — verbatim opening and closing lines, bullet scripts in the
middle, every handoff named.
