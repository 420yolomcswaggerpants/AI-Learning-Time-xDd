# Day 40 Progress: First Tester Feedback, Clearer Wording, A Job Agent That Keeps Up

## What I Did Today

### Study and Review
- Continued daily concept and vocabulary study, as always.

### Done

This covers everything since the last note: the evening after it, and today.

**The first written feedback from a tester, acted on.**
- **Multiple-choice questions that gave the answer away.** A tester wrote that several questions had wrong choices so far off that the right one stood out without working anything out. Now at most one wrong choice is far from the answer. Measured across every year level: questions with two or more far-off choices went from 10 to 42 percent, depending on the year, to 0.2 percent or less.
- **The starting check felt random to a strong tester.** Partway through a run of right answers, a question from an earlier year appeared. It was rebuilt so its order makes sense to the person taking it. Simulated against the old version on the real content before it was built.
- **A topic assumed something it never said.** Another tester noticed that one section's questions only made sense if you already knew a detail they never stated. The questions now state it, and two section titles say it too. Wording only; no answer changed, and nobody's progress moved.

**Smaller fixes from watching the first round.**
- **Adding a learner now says clearly which parts are for the parent and which are for the child.** It read as if both were one person.
- **An agreement was being shown twice.** It is shown once now, and stays linked at the bottom of every page.
- **Written directions became links.** No sentence tells anyone to go here, then there, then there, where a link can take them.
- **An optional help button sat on screen at a moment it got in the way.** It now waits for the next step.
- **The feedback after a mistake was reworded,** and now shows what was entered beside the right answer.
- **Sign-ups through an invite now have their own allowance.** A shared network can no longer block a tester, as it did once before.

**The job agent, checked and made to keep up.**
- Ran it once after cutting its access back. It worked end to end in twelve minutes: no new roles, a tailored resume for each role already waiting, and a fresh general one. One web page waited for a permission nobody was there to give, and the run carried on without it.
- **Its facts about me had gone stale:** an old test count, and "testers haven't started yet". Corrected them, and gave it one new step: at the start of every run it reads my newest daily note and updates its numbers from it. Only figures the note states plainly, never estimated.
- **Gave it less access, not more.** It no longer gets a copy of the product code, which it never needed, and it treats the notes as read-only.

**Verification and deployment.**
- Three commits since the last note, all pushed and live. No schema changes. Production error log empty.
- Product document 0.79 to 0.83, technical document 0.59 to 0.62.

### Decided
- **Act on tester feedback the same day,** while the tester still remembers what they meant.
- **Simulate before changing the starting check,** as with anything tuned.
- **Let the job agent read my notes for its numbers,** but never edit my facts or my resume. It keeps its own copy of the figures, and I keep mine.
- **No new access for the agent to keep it current.** It already had the notes; it lost the code.

### Noticed
- **Testers see what no checker measures.** "The right answer is obvious" and "it never said that" are both things a person notices in seconds and a script never looks for.
- **A fix can be correct and still feel wrong.** The starting check worked before; to the person taking it, the order looked random, and that mattered too.
- **An agent's facts go stale the same day.** A resume line written yesterday was already behind.
- **Updating the agent's setup replaces all of it.** Leaving out one part dropped it. Comparing the saved setup to what I meant to send caught it at once, and it was restored before any run.

## Numbers
- 942 automated tests across 102 files, all green
- Content checker green: 1,249 items, 3.75 million generated questions checked
- 3 commits since the last note, 32 files, +461 / −89 lines, 3 test files among them
- 0 schema changes
- Product document 0.79 to 0.83, technical document 0.59 to 0.62

## Next
- Reply to both testers who wrote in.
- Each day: read what testers sent and what the record shows.
- Confirm the newest fixes on my own phone.
- Run the job agent once and check it picked up today's numbers from this note.
- The automatic dependency update, once testing has settled.

## Current Status
- Testers are playing. Every piece of feedback so far is fixed and live, and the production error log is empty.
- The job agent is current and narrower than before.

## Key Reflections
- **A tester's sentence is worth a day of checks.** Each note pointed at something real, and each fix was small once it was named.
- **Fix the feeling, not just the fault.** Something can be right by every measure and still look broken to the person using it.
- **Keep an agent current from one source.** One place that changes every day beats facts copied by hand into several.
- **Check the whole thing after you change part of it.** A replace that looks like an edit is how a setting quietly disappears.
