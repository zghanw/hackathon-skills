# hackathon-skills

**Turn a hackathon problem statement into a scored solution, a polished demo, a deck, and a timed pitch script split across your team — before the deadline eats you alive.**

![License](https://img.shields.io/github/license/zghanw/hackathon-skills?style=flat-square&color=111111)
![Claude Code](https://img.shields.io/badge/works%20with-Claude%20Code-5A4FCF?style=flat-square)
![Skills](https://img.shields.io/badge/skills-3%20focused%2C%20not%2040-111111?style=flat-square)

It's midnight, the demo half-works, nobody's started the slides, and the judges want you on stage in six hours. That's the exact moment this repo is for.

## What you get

3 focused Claude Code skills that cover the part of a hackathon nothing else does well, plus a guide that tells you exactly which *other* skill to reach for at every other step:

- **`/hackathon-kickoff`** — feed it the problem statement and the judging rubric. It works out what actually earns points, drafts the "why this is urgent" hook your pitch needs, and lays out a phase plan against your deadline.
- **`/hackathon-flow`** — lost track of what phase you're in at 3am? It looks at what's already in your repo and tells you the next move.
- **`/pitch-timebox`** — give it your time limit and your team's names. It splits the script into timed, per-person sections with handoff lines, a Q&A cheat sheet, and a rehearsal checklist — so nobody freestyles on stage.

## Built lean on purpose

A lot of "awesome Claude skills" repos are 40, 150, sometimes 2,000+ skills in a single install. Every skill's name and description has to sit in context so Claude can decide when to trigger it — that's tokens spent on every message, for skills you'll never open during a 24-hour hackathon. You don't need a regulatory-compliance skill or a SaaS-metrics skill to ship a weekend project.

This repo ships **3 skills**, not a bundle. For everything else — brainstorming, UI, QA, the actual deck — [SCENARIOS.md](SCENARIOS.md) tells you the one skill that fits your situation, and you install only that. Lean by default, not by discipline you have to maintain yourself.

Claude Code plugins can declare hard `dependencies` that auto-install and auto-enable alongside your plugin. This repo deliberately doesn't declare superpowers, gstack, or ui-ux-pro-max as dependencies — doing that would force-install a 13-skill methodology, a QA/ship suite, and a full style library on every team regardless of whether they need any of them, which is the exact bloat this section argues against. The 3 skills here do name their companions explicitly (check each `SKILL.md`'s "Prerequisites" section) so you know what to add and when, without anything being installed for you.

<details>
<summary>Why doesn't this just bundle those other skills too, then?</summary>

Claude Code marketplaces *can* pull plugins from other repos (`source: {source: "git-subdir", url, path, ref, sha}` — this is how Anthropic's own official marketplace bundles Adobe's and 42Crunch's skills). This repo doesn't do that yet, because that schema needs a commit pinned per dependency and breaks silently if the upstream repo restructures. Rather than guess at pins I hadn't verified, the companion installs below are copy-paste commands instead. PRs that add verified pins welcome.
</details>

## Install

```
/plugin marketplace add zghanw/hackathon-skills
/plugin install @hackathon-skills
```

That's it — you now have `/hackathon-kickoff`, `/hackathon-flow`, and `/pitch-timebox`.

## The pipeline

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

Full situation → skill breakdown, including every companion skill by name, is in [SCENARIOS.md](SCENARIOS.md).

### Companion installs

Install only the ones your team actually needs this hackathon:

```
# Brainstorming through actual implementation (spec → plan → TDD build)
/plugin install superpowers@claude-plugins-official

# UI polish: styles, color palettes, font pairings, component patterns
/plugin marketplace add nextlevelbuilder/ui-ux-pro-max-skill
/plugin install ui-ux-pro-max@ui-ux-pro-max-skill
```

```
# QA, design review, shipping — NOT a Claude Code plugin, installs straight into ~/.claude/skills
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/.claude/skills/gstack && cd ~/.claude/skills/gstack && ./setup
```

Verified directly against each project's current source as of July 2026, so this won't match every guide you find online:

- `superpowers` is on Anthropic's official marketplace (`claude-plugins-official`), which most Claude Code installs already have registered, so it skips the `marketplace add` step. It's more than brainstorming — it's a full spec → plan → build pipeline with mandatory TDD and per-task review, real engineering rigor that can also cost hours a hackathon doesn't have. Use its `brainstorming` and `writing-plans` skills either way; for the actual build, weigh that rigor against just building off the plan without the enforced test loop.
- `gstack` **is not currently a Claude Code plugin** — its repo has no `.claude-plugin` manifest despite some third-party mirrors and older posts claiming a `/plugin marketplace add garrytan/gstack` install. The command above is the one its own README documents today; it clones into `~/.claude/skills/gstack` and runs a setup script, no marketplace involved. Re-run `./setup` after every `git pull` to pick up updates.
- `ui-ux-pro-max`'s marketplace install has a known bug on some setups ("Zip file contains a symbolic link") — if `/plugin install` fails with that error, fall back to its CLI: `npm install -g ui-ux-pro-max-cli && uipro init --ai claude`.

Anything drifts again by the time you read this — that's the nature of fast-moving community repos, not a one-time fact. Re-check the source repo's own README before relying on an install command, here or anywhere else.

For the deck itself, pick one based on what judges want:
- **Zero-dependency HTML deck** with a built-in narration script and live-demo slots: [Esther2524/beautiful-hackathon-slides](https://github.com/Esther2524/beautiful-hackathon-slides)
- **An actual `.pptx` upload**: the `pptx` skill from [anthropics/skills](https://github.com/anthropics/skills) (often already bundled in your Claude environment)

## Who this is for

Students and small teams doing hackathons — where there's no ops team, no dedicated designer, and the same four people have to write the code, design the deck, and deliver the pitch before a hard deadline. If that's your Saturday, this is for you.

## Contributing

Found a phase this doesn't cover well, or a companion skill that deserves a spot in [SCENARIOS.md](SCENARIOS.md)? PRs and issues welcome — this is meant to grow with whatever the community finds actually wins hackathons, not just what one person's team needed once.

If this saved your team an hour of scrambling, a ⭐ helps the next team find it before their deadline.

## Prior art

[fshot/claude-plugin-hackathoner](https://github.com/fshot/claude-plugin-hackathoner) is a more opinionated, single-plugin take on this same problem (`/hackprep` covers research, team roster, brainstorm, scaffold, slides, video, and demo prep end to end). Worth a look if you want one all-in-one plugin instead of composing smaller pieces.

## License

MIT — see [LICENSE](LICENSE).
