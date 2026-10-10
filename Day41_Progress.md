# Day 41 Progress: A Planned Build Shipped, Every Year Level Reviewed, First-Look Fixes

## What I Did Today

### Study and Review
- Continued daily concept and vocabulary study, as always.

### Done

This covers everything since the last note: the evening after it, and today.

**A planned set of features, designed first and then built.**
- **Designed the evening before, in the documents, not in code.** Each feature got its rules, its place in the technical design, and an order to build in. The agents' roles and stages were written down too, so every agent worked from the same instructions.
- **Built in stages with three kinds of agent:** builders for code, writers for learning content, and independent reviewers who never check their own work. At most three ran at once, and never two on the same year level.
- **Every tuned number came from simulation.** For each one I chose from two or three simulated options, with a note on which were hard on struggling learners.
- **A settings area for accessibility:** volume, text size, reduced motion, high contrast and a reading font, all remembered on the device.

**The learning content, audited and filled in.**
- **An audit of every year level against the curriculum standard** found gaps inside the main work of several years. 23 new topics fill them, each with its worked examples, and each asked in a form that can be marked exactly.
- **New kinds of pictures** where a classroom would draw one: data displays and more shapes, each described in words for screen readers.
- **Thin topics got more variety,** so a learner doesn't meet the same question twice in a row.

**An independent review of every year level.**
- **One reviewer per year level** regenerated many thousands of questions and recomputed each answer from what a learner actually sees. **No wrong answers were found anywhere.**
- **What they did find:** questions whose answer could be guessed without working anything out, such as a count that was almost always the same number, or a right answer that always sat in the same place among the choices. Each was spread out and re-measured.
- **Shared fixes that came out of it:** a choice can no longer fall outside the scale of the picture it is read from, two choices can never be worth the same, and screen-reader descriptions no longer give an answer away.

**Checked in a browser and by a security review.**
- **Larger text on a phone pushed parts of the screen off the edge,** including a way back to the settings. Fixed where each overflow happened, with a safety net behind it.
- **A read-only security and privacy review** found nothing high or medium. The two low findings a learner could notice were fixed the same day.
- **Re-measured how hard things are for the youngest learners.** They had become easier than the documents said, so I tightened them one step, chosen from simulated options. They are still gentler than for older learners.

**My own first look, acted on the same day.**
- **Too much to read in one place.** Choices are now a picture, a plain name and a few words, with the full sentence kept for read-aloud.
- **Two names didn't say what they do,** and some descriptions used percentages, which the youngest learners haven't met. Both names were replaced, and the descriptions are plain words now.
- **The music for one part of the experience didn't fit it.** That part has its own now.
- **I couldn't find a feature I had just used.** It is now shown on the main screen.
- **An admin command for my own test account,** through the same audited, permission-scoped path as every other admin action.

**Verification and deployment.**
- Six commits since the last note, all pushed and live. Four schema changes, all additive. Production error log empty.
- Product document 0.83 to 0.89, technical document 0.62 to 0.67.

### Decided
- **Design in the documents before any code,** with the agents' roles written down where every agent reads them.
- **Numbers go to me as simulated options,** never picked by an agent.
- **A reviewer is never the author.** Every year level was checked by someone who didn't write it.
- **Fix what a first look finds the same day,** the same rule as for testers.

### Noticed
- **The biggest problems weren't wrong answers, they were guessable ones.** Nothing was marked wrong, but several questions could be answered without the work, and only measuring the spread showed it.
- **A screen reader can give away what the eye can't.** A description written to help was naming the answer.
- **A restart can quietly change what a test run means.** After a reboot the local database didn't come back, and the first full run passed while skipping a third of the tests. A pass with skips is not a pass.
- **Doing it from memory makes duplicates.** The automatic hourly continue job ended up scheduled twice after the restart, and both fired every hour until I listed them.
- **Too much reading is a bug, not a style.** The words were correct, and still too many for the youngest learners to get through.

## Numbers
- 1,256 automated tests across 125 files, all green
- Content checker green: 1,564 items, 4.69 million generated questions checked
- 6 commits since the last note, 260 files, +36,165 / −1,168 lines, 39 test files among them (25 new)
- 4 schema changes, all additive
- Product document 0.83 to 0.89, technical document 0.62 to 0.67

## Next
- Replace the AI feature's API key before it expires, then retire the old one.
- Play through the new build myself on a phone.
- Send the new build to the testers and read what comes back.
- Run the job agent once and check it picked up today's numbers.
- The automatic dependency update, once testing has settled.

## Current Status
- The planned build is live, every year level has been independently reviewed, and the production error log is empty.
- Everything I found on my own first look is fixed and live.

## Key Reflections
- **Write the plan where the agents read it.** One set of instructions kept many agents consistent across a long day.
- **Measure the spread, not just the correctness.** A question can be right every time and still be answerable without thinking.
- **A green run only counts if nothing was skipped.** Check what ran, not just the result.
- **Use it yourself early.** Five minutes of my own use found things a day of checks did not.
