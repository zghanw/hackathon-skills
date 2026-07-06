# PITCH.md — Team EcoEats @ HackTheWaste 2026

<!-- FICTIONAL WORKED EXAMPLE — output of /pitch-timebox, shown so you know
     what the skill produces before you run it. -->

**Time limit:** 5 min pitch + 2 min Q&A
**Word budget:** ~640 words (5 min × 142 wpm, minus 10% buffer)
**Speakers:** Priya → Maya → Alex → Jun

## Timing table

| Start–End | Speaker | Section | Words | Script | Handoff line |
|---|---|---|---|---|---|
| 0:00–0:45 | Priya | Hook + urgency | ~100 | VERBATIM: "Every night at 9pm, our dining halls do something insane. They take 340 kilograms of perfectly good food — 900 meals — and throw it in the dumpster. Meanwhile, one in four students on this campus skipped a meal this week to save money. Those two facts are 400 metres apart. We built the bridge." Then: audit source, one sentence; tonight's number, one sentence. | "…and Maya is going to rescue a meal for you, live, right now." |
| 0:45–3:00 | Maya | Live demo | ~280 | Bullets: post surplus as dining-hall staff (one tap) → Jun's phone buzzes ON STAGE, hold it to the mic → claim it → counter ticks to 1 → show geofence map, "only people who can walk there before closing get the alert" → post second item, audience-visible counter ticks again. ⚠ fallback: `demo-backup.mp4` | "That claim window Alex designed is the clever part — Alex, why rationing by walk-time works." |
| 3:00–4:00 | Alex | Impact + model | ~140 | Bullets: zero price but rationed by arrival-time = no hoarding, no waste-chasing apps' spam problem → campus-wide math: 340 kg/day × semester = ~61 tonnes, 110k meals → dining halls save disposal fees, students eat free — nobody pays until we add a second campus. | "So it works for one campus. Jun, what does it take to make it every campus?" |
| 4:00–4:45 | Jun | Team + ask/close | ~100 | Bullets: built in 24h — working push, geofence, deploy; each of us owned one layer. Next 30 days: pilot with our actual dining services (email drafted). VERBATIM CLOSE: "340 kilograms a night. We stopped counting it as waste and started counting it as dinner. We're EcoEats — come claim a meal." | — |
| 4:45–5:00 | — | Buffer | — | Breathing room for applause, stumbles, walking to the mic. | — |

## Demo fallback

- Backup recording: `demo-backup.mp4` (90s, captions burned in, plays with sound off).
- Who triggers it: Maya, the moment the push notification takes >10 seconds
  to arrive. Line: "While that travels — here's the same flow recorded an
  hour ago." No apologizing.

## Q&A prep

| Likely question | One-line answer | Who answers |
|---|---|---|
| "Is that push notification real or mocked?" (Tech, 25%) | Real: Firebase Cloud Messaging to a physical device — here's the delivery log timestamp. | Jun |
| "What stops one student claiming everything?" (Innovation, 25%) | Claim windows: 2 active claims max, and unclaimed food re-alerts the next radius ring at closing minus 20 min. | Alex |
| "How do you know 340 kg is accurate?" (Impact, 30%) | Campus sustainability audit, spring 2026, table 4 — we brought the PDF. | Alex |
| "Why won't dining halls just ignore this?" (Impact, 30%) | Posting is one tap and cuts their disposal fees; we've drafted the pilot email with the sustainability office's own audit numbers. | Priya |
| "What's the business model?" (viability) | Free for our campus forever; per-campus licence to other universities' dining contractors — they already pay per-kg disposal. | Jun |
| "What did you cut?" (execution) | Accounts — magic-link claims saved 3 hours and judges never miss login screens. | Maya |

## Rehearsal checklist

- [x] Full run #1 — 5:12 → cut geofence explainer from 3 sentences to 1
- [x] Full run #2 — 4:41 ✓
- [x] Every handoff line lands (next speaker starts within 2 seconds)
- [x] `demo-backup.mp4` plays on the presenting laptop, offline
- [x] Each Q&A owner answered their question cold, out loud, once
- [ ] Presenting machine: notifications off, tabs closed, charger packed — do at venue
