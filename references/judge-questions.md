# The questions judges actually ask

Fifteen questions that come up at nearly every hackathon, grouped by the
rubric criterion they're really probing. `/pitch-timebox` pulls from this
list when building your Q&A prep sheet: prioritize the group matching your
**weakest** criterion, because that's where judges dig.

Each question has a prep line: what a strong answer contains, not a script.

## Impact ("does this matter?")

1. **"Who exactly is this for, and how many of them are here?"**
   Prep: a named user group + a local number you can defend. "Students" is
   weak; "the 1 in 4 students who skipped a meal this week, per the campus
   audit" survives follow-ups.
2. **"What changes for them the day this exists?"**
   Prep: one before/after sentence. If the answer needs two sentences, the
   product isn't focused enough; fix the pitch, not the answer.
3. **"Where did that number come from?"**
   Prep: name the source out loud (audit, dataset, interview count). Bring
   the source. A judge who catches one invented number distrusts every slide.

## Technical execution ("what did you actually build?")

4. **"Is that live or mocked?"**
   Prep: answer honestly and precisely: "the push is real, the second
   dining hall is seeded data." Judges forgive mocks; they don't forgive
   discovering one.
5. **"What did you build versus call an API for?"**
   Prep: one sentence claiming the part you're proud of, one crediting the
   APIs. Trying to take credit for the API is the classic own-goal.
6. **"What breaks first at 10× users?"**
   Prep: name the actual bottleneck (the geofence query, the free-tier
   queue). "It scales" is the wrong answer at every hackathon, ever.

## Innovation ("why hasn't someone done this?")

7. **"What's the closest existing tool, and why isn't it enough?"**
   Prep: name a real competitor yourself; naming it first turns a gotcha
   into a comparison you control.
8. **"What's the one thing here someone couldn't clone in a weekend?"**
   Prep: usually not code; it's the mechanism, dataset, or relationship
   (the claim-window design, the dining-services pilot email).

## Viability ("who pays?")

9. **"What's the business model?"**
   Prep: one plausible payer + what they already pay for the problem today
   (disposal fees, overtime, churn). Don't project revenue; point at an
   existing budget line.
10. **"What does this cost to run per user?"**
    Prep: rough unit cost from your actual stack ("free tier to 5k users,
    then ~$0.002/alert"). Precision signals you deployed it for real.

## Execution under constraint ("can this team ship?")

11. **"What did you cut, and why?"**
    Prep: this is a gift; answer with your scope-cut log. Teams that cut
    deliberately read as senior; teams that "ran out of time" read as junior.
12. **"What would you do with 30 more days?"**
    Prep: one concrete next step already in motion (a drafted pilot email
    beats "add more features").
13. **"Who built what?"**
    Prep: every member answers for their own layer in one sentence. A team
    where one person answers everything reads as one person's project.

## The demo-moment traps

14. **"Can you show that again with different input?"**
    Prep: have a second path rehearsed (different item, different radius).
    A demo that only works one way looks like a recording.
15. **"What happens with bad input?"**
    Prep: show the guard, don't describe it; type the garbage yourself
    before the judge asks to.

---

**The meta-rule:** judges ask questions to find the edge of what's real.
Every answer that names a source, a number, a cut, or a limitation moves the
edge further out than they expected: that's what scoring "above expectation"
literally is.
