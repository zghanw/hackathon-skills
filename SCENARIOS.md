# Scenarios: which skill to invoke when

A hackathon has one non-negotiable input (a deadline) and one scoring
function (the rubric). Everything below is organized around those two facts.
"This repo" = the 3 skills shipped here. Everything else is a companion
install, not a hard dependency — see [README.md](README.md#companion-installs)
for exact install commands and caveats. If a row below names a skill you
haven't installed yet, install it when you reach that row, not before.

| Situation | Invoke | Why |
|---|---|---|
| Problem statement + rubric just dropped, nothing built yet | `/hackathon-kickoff` (this repo) | Scores candidate angles against the rubric *before* anyone writes code, and drafts the urgency hook the whole pitch will hang on. |
| You have an angle but not a concrete solution/spec | `superpowers` (`brainstorming` skill) | Turns a rough idea into a fully-formed spec through natural back-and-forth, not a monologue. |
| Spec's approved, need someone to actually write the code | `superpowers` (`writing-plans` → `executing-plans`/`subagent-driven-development`) for full TDD rigor and per-task review; or build straight off the plan without the enforced test loop | Full red/green TDD plus two-stage review per task is built for production code — it can cost more hours than a throwaway demo has. Pick rigor vs. speed based on how closely judges will read your code vs. just watch it run. |
| Solo or tiny team, brutal deadline (e.g. 24h), want hard phase gates | `devcon-hack-coach` (mertpaker) | Spec-first, refuses to let you code before a one-page spec exists; four gated phases with named checkpoints. |
| Building the demo app's UI | `ui-ux-pro-max` | 50+ styles, 161 palettes, 57 font pairings, component patterns across React/Next/Vue/Svelte/SwiftUI/RN/Flutter/Tailwind/shadcn. Use before reaching for a new UI dependency. |
| App works but looks like a hackathon project | gstack `/design-review` or `/design-consultation` | Designer's-eye pass: spacing, hierarchy, "AI slop" patterns, slow interactions. |
| Need to find and fix bugs before judging | gstack `/qa` | Systematic QA, fixes with atomic commits, auto-generates regression tests per fix. |
| Pre-landing sanity check on a branch/PR | gstack `/review` | SQL safety, trust-boundary issues, structural review before you ship. |
| Time to build the slide deck, want zero dependencies + a narration script | `beautiful-hackathon-slides` (Esther2524) | Purpose-built for hackathon demo decks: 9-phase workflow, 5 style previews, reserves slots for live-demo recordings, generates an AI narration script for you. |
| Judges specifically require an uploaded `.pptx` | the `pptx` skill (anthropics/skills, or already bundled in your environment) | Native, editable PowerPoint output. |
| Want video + deck + landing page from the same codebase | `pitchkit` (EricSun0218) or `fluiddocs-deck-builder` (FluidForm-ai) | One pass turns a repo into a promo video, `.pptx`, and a single-file landing page (pitchkit), or gives you brand-mirror deck templates + PDF/PPTX import (fluiddocs). |
| Deck exists, narrative feels weak or unfocused | `winning-pitch-deck` (0xbenbottle, DePitch review mode) or `dkorobtsov/pitch-deck` audit phase | Scores an existing deck/script against a rubric and returns the top 3-5 fixes — not a rewrite. |
| Given N minutes and M teammates, need to know who says what and when | `/pitch-timebox` (this repo) | Slices the word budget by rubric weight, assigns contiguous speaker blocks with handoff lines, drafts Q&A prep, produces a rehearsal checklist. |
| Q&A is in an hour and you don't know what judges will ask | [references/judge-questions.md](references/judge-questions.md) (this repo) | The 15 questions judges actually ask, grouped by rubric criterion, each with what a strong answer contains. |
| Not sure what phase you're in / what to do next | `/hackathon-flow` (this repo) | Reads what already exists in the repo (`HACKATHON.md`, app code, deck, script) and points at the next skill. |
| Final hour before pitching | gstack `/qa-only` (dry run, no fixes) + `/pitch-timebox`'s rehearsal checklist | Confirms the live app still works and the timing holds without touching code. |

## Full pipeline at a glance

```
problem statement + rubric
        │
        ▼
  /hackathon-kickoff  ──────▶  HACKATHON.md (angle, urgency hook, phase plan)
        │
        ▼
  superpowers: brainstorming  ──▶  concrete spec
        │
        ▼
  superpowers: writing-plans → executing-plans  ──▶  Feature Zero, then features
        │        (or build straight off the plan, skip the TDD loop, if faster)
        ▼
  ui-ux-pro-max (UI polish)  ──▶  gstack /design-review, /qa
        │
        ▼
  beautiful-hackathon-slides  or  pptx skill  ──▶  deck (+ narration script)
        │
        ▼
  /pitch-timebox  ──────▶  PITCH.md (timing, speakers, Q&A, rehearsal)
        │
        ▼
  gstack /qa-only dry run  ──▶  go pitch
```

## What the outputs look like

Both artifact-producing skills fill in the templates at
[templates/](templates/) and there's a complete fictional worked example — a
24h campus hackathon, 4 teammates, 5-minute pitch — at
[examples/ecoeats-24h/](examples/ecoeats-24h/). Read it before your first
kickoff; it's faster than any explanation of what the skills do.

## Prior art worth knowing about

[fshot/claude-plugin-hackathoner](https://github.com/fshot/claude-plugin-hackathoner)
already implements a very similar end-to-end methodology (`/hackprep
init/research/team/brainstorm/scaffold/checkpoint/slides/video/demo`, plus a
per-teammate `/hack` that picks up an assigned issue, plans it, builds it in
a worktree, and opens a PR) as one plugin. The "Feature Zero" term used above
— one thin end-to-end slice before individual features — is its checkpoint
pattern, credited here rather than reimplemented. If you want a single
opinionated all-in-one instead of composing the skills above, it's worth
comparing against before you invest further here.
