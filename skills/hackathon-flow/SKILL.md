---
name: hackathon-flow
description: Router for the hackathon pipeline. Looks at what already exists (HACKATHON.md, source code, a deck, a script) and says which skill or command to invoke next. Use when a team isn't sure what phase they're in or what to do next.
---

# Hackathon Flow

A thin router, not a state machine: it infers phase from what's already on
disk and points at the right skill. No progress file to maintain beyond the
`HACKATHON.md` that `/hackathon-kickoff` already writes.

## Prerequisites

None to run the router itself. The skills and commands it points to below
aren't hard dependencies of this plugin; check `/plugin` before assuming one
is installed, and fall back to the companion-install commands in
[README.md](../../README.md#companion-installs) if it isn't.

## How to use it

1. Check for `HACKATHON.md` in the repo root.
   - Missing → team hasn't done kickoff yet. Run `/hackathon-kickoff` first;
     nothing downstream should start before the rubric-aligned angle exists.
2. Check for a fleshed-out spec / feature list beyond the one-line angle.
   - Missing → hand off to `superpowers`' `brainstorming` skill to turn the
     angle into a concrete, buildable spec through dialogue, then its own
     `writing-plans` skill to break the spec into a task-by-task plan.
3. Check for an app (package.json, src/, etc.) with working core features.
   - Nothing yet → don't build features one at a time. Get a **Feature Zero**
     working first: one thin end-to-end slice, mock data is fine, deployed
     and demo-able, so there's always something to show no matter when time
     runs out. `superpowers`' `executing-plans`/`subagent-driven-development`
     builds this with full TDD rigor and per-task review; for a throwaway
     hackathon demo that ceremony often costs more time than it buys, so
     building straight off the plan without the enforced test loop is a
     reasonable, faster alternative. `ui-ux-pro-max` covers UI polish either
     way. Don't reach for a new UI dependency it already covers.
   - Exists but rough → gstack `/design-review` for a polish pass, gstack
     `/qa` to find and fix bugs with regression tests before anything else.
4. Check for a deck file (`.pptx`, `deck.html`, `slides.md`, etc.).
   - Missing → deck phase. Two branches:
     - Need a browser-native, zero-dependency deck with live-demo slots and
       an auto-generated narration script → `beautiful-hackathon-slides`.
     - Judges require an uploaded `.pptx` → the `pptx` skill (from
       `anthropics/skills`, or already bundled if your Claude environment
       ships it).
   - Exists but the narrative feels weak → run it through `winning-pitch-deck`
     (DePitch review mode) or `dkorobtsov/pitch-deck`'s audit phase for a
     prioritized fix list, not a rewrite.
5. Check for a pitch script with per-speaker timing.
   - Missing and a deck/narration script exists → `/pitch-timebox` (this
     repo) slices the existing script across the team's time limit and
     roster rather than writing a new one from scratch.
   - Missing entirely → `/pitch-timebox` also works from just the
     `HACKATHON.md` angle + urgency hook if no deck exists yet.
6. Everything above exists → rehearsal. gstack `/qa-only` for a dry-run pass
   over the live app, plus the rehearsal checklist `/pitch-timebox` produced.

## Reference

For situation → skill lookups outside this linear flow (e.g. "the judges
changed the time limit an hour before pitching," "we need to re-pick roles"),
see [SCENARIOS.md](../../SCENARIOS.md) at the repo root.
