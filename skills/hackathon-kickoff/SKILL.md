---
name: hackathon-kickoff
description: Turn a hackathon problem statement and judging rubric into a scoring-aligned solution angle, an urgency narrative hook, and a time-boxed phase plan. Use at the very start of a hackathon, right after the problem statement and marking scheme are released, before any brainstorming or code.
---

# Hackathon Kickoff

Judges score against a rubric, not against "cool tech." This skill reads the
problem statement and marking scheme first and works backward from what
actually earns points, before anyone touches an editor.

## When to activate

- A problem statement + judging criteria / marking scheme just dropped.
- Someone asks "what should we build" or "how do we make this urgent" before a solution exists.
- Re-run mid-hack if the team pivots and the angle needs re-scoring.

## Prerequisites

Nothing required to run this skill itself. The phase plan it produces names
companion skills for later phases (`superpowers`, `ui-ux-pro-max`, `gstack`) —
none of them are hard dependencies of this plugin, on purpose (see
[README: Built lean on purpose](../../README.md#built-lean-on-purpose)).
Install each only when you actually reach that phase.

## Inputs to gather

Ask only for what's missing:

1. The problem statement (paste or file).
2. The judging rubric / marking scheme, with weights if published.
3. Total hackathon duration and the hard submission deadline.
4. The pitch time limit judges give (e.g. "5 minutes + 2 min Q&A").
5. Team roster (names, and any strong suits worth routing work to).

## Workflow

1. **Extract criteria verbatim.** List every judged dimension with its weight.
   If no weights are published, ask the team to gut-rank them 1st/2nd/3rd —
   don't silently assume equal weight.
2. **Reverse-engineer what wins.** For each criterion, write the concrete,
   demo-able proof point a judge could point at in 30 seconds ("technical
   difficulty" → "live on-device inference, not a canned API call").
3. **Draft 2–3 candidate angles**, each scored against the weighted rubric
   (rough 1–5 per criterion, not decimals — this is a gut-check, not a model).
   Pick one with the team; don't pick for them.
4. **Craft the urgency hook.** One sentence naming the concrete stakes of
   *not* solving this now — a cost, a number, a specific person or scenario
   it happens to. Judges fund urgency, not features. Avoid generic framing
   ("this is a growing problem") — name who it hurts and how much.
5. **Build the phase plan.** Split total hackathon time into checkpoints and
   name which skill covers each (see table below). Back-solve from the
   submission deadline and the pitch time limit, not forward from hour zero.
   Default to a **Feature Zero** checkpoint early: one thin end-to-end slice
   (mock data is fine) deployed and demo-able before any individual feature
   is built, so there's always something to show no matter when time runs out.
6. **Write `HACKATHON.md`** in the repo root by filling in
   `${CLAUDE_PLUGIN_ROOT}/templates/HACKATHON.md` — every section, including
   the team table (who owns which build layer AND which pitch section) and a
   pre-agreed scope-cut list decided now, while calm, not at 4am. Every later
   phase (brainstorming, deck, `/pitch-timebox`) reads this file so the story
   stays consistent end to end. A fully worked example:
   `${CLAUDE_PLUGIN_ROOT}/examples/ecoeats-24h/HACKATHON.md` — match its
   specificity, especially the demo-able proof point per criterion.

## Phase handoff

| Checkpoint | Phase | Invoke |
|---|---|---|
| T+0 | Kickoff (this skill) | `/hackathon-kickoff` |
| next ~15% | Solution design | `superpowers` (`brainstorming` → `writing-plans`) turns the angle into a spec, then a task-by-task plan |
| through ~65% | Build the demo (Feature Zero, then features) | `superpowers` (`executing-plans`/`subagent-driven-development`) for full TDD rigor, or build straight off the plan without the enforced test loop if that's too slow for a throwaway demo; `ui-ux-pro-max` for UI polish either way |
| ~65–80% | QA pass | gstack `/design-review`, `/qa` |
| ~80–90% | Deck + script | `beautiful-hackathon-slides` (HTML) or the `pptx` skill (native PowerPoint) |
| ~90–95% | Pitch timing + roles | `/pitch-timebox` (this repo) |
| ~95–100% | Rehearsal | gstack `/qa-only` dry run + `/pitch-timebox` rehearsal checklist |

Don't run every phase in strict sequence — `/hackathon-flow` (this repo) can
be invoked any time to re-orient on what's next given what already exists in
the repo.
