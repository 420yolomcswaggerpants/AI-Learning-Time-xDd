# Day 31 Progress: Content Coverage Tripled, Multi-Level Profiles, Opt-In Audio

## What I Did Today

### Study and Review
- Continued daily concept and vocabulary study, as always.

### Shipped (committed locally as c7cedb7, not yet pushed)

**Content coverage tripled.**
- Three more year levels of learning content were written, reviewed by independent readers, and shipped.
- Coverage went from **three year levels to six**.
- The youngest levels received illustrated prompts so they can be used without reading.

**One learner, one profile, any year level.**
- A family can now move a learner between year levels without setting up a new profile.
- Everything earned is kept intact — levels, medals, exams, all history.
- The previous year level's map is exactly as they left it.
- Any year level they don't have access to is refused, with the reason shown to the parent — **never a price shown to the child**.
- Finishing a year level tells the child the next one is ready and to ask a grown-up.

**Each year level is its own environment.**
- Map and arena change colour and scenery by year level.
- Each year level has its own enemy family, including a placeholder family for year levels not yet written.
- A bought map theme recolours whichever environment the learner is currently in.
- **Nothing in the store is locked by year level** — the PRD now states this explicitly.

**Audio is now opt-in.**
- Read-aloud is a button ("Read it to me"), on by default for the youngest levels and for anyone who turns it on.
- Reading each question automatically is a separate choice in the student menu, off until the learner picks it.
- Short sound effects were added, with a mute.

**Parent view.**
- Shows the curriculum code beside each topic that needs practice.

**Operations.**
- A daily spending ceiling was added for the AI feature.
- A competitor benchmark was published in the internal documents.
- Production was deployed and verified.

**Dev tooling.**
- Admin scripts now write the same subscription row a payments webhook will, so an account opens every year level through the **real access check**, and revoke ends it with the real consequences.

### Verified
- **574 tests, all green.**
- Content checker, simulator, lint, build with leak check — all clean.
- A headless drive confirmed the full flow: saw a locked year level, granted access, moved a learner between levels, and revoked it back — with no errors.
- All six year-level maps and all seven arenas were checked by eye.
- Four commits, all tests green.

## The Unexpected Find
- The headless drives revealed that headless Chromium on Windows can reach the speech engine — a kindergarten screen was **reading its prompts out loud during automated testing**.
- Every drive now mutes speech before it opens a page.
- The app itself no longer speaks unless asked.
- This was only discovered because the drives ran the real thing rather than a stub.

## Numbers
- 574 automated tests, all green
- Content coverage: 3 → 6 year levels
- 4 commits
- Committed locally, **not yet pushed**

## Open / Next
- Push the commit and redeploy.
- Continue with remaining year levels.
- Keep the audio behaviour opt-in as more content ships.

## Current Status
- Learning content doubled in coverage; youngest levels usable without reading.
- Multi-level learner profiles working end to end through the real access check.
- Audio is opt-in and muted in automation.
- Daily spending ceiling in place for the AI feature.
- Production deployed and verified.

## Key Reflections
- **Independent review of content scales better than self-review.** Three more year levels went out with outside readers checking them, not just the author.
- **Access control should be tested through the real path, not a shortcut.** Writing the same row a payment webhook would write means the test exercises the actual access check, not a bypass.
- **Refusals should be explained to the buyer, never priced to the user.** A child should never see a paywall — only an adult should see the reason.
- **Automation caught a behaviour no human would have reported.** A screen talking during a headless run is invisible in a browser and obvious in a log. The fix was in the harness, and it also made the app itself quieter.
- **Default-on versus opt-in matters for audio.** Something that happens *to* a learner is different from something they choose. The default flipped, and the app got less intrusive without losing the feature.
- **Store content should not be gated by progress.** Cosmetic items crossing every year level keeps the reward system about expression, not advancement.
