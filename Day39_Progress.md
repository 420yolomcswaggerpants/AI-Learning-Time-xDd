# Day 39 Progress: First Testers, Live Settings, Three Fixes

## What I Did Today

### Study and Review
- Continued daily concept and vocabulary study, as always.

### Done

**The prototype went out.**
- Sent to a few people to test, through an invite link that needs nothing opened by hand. My own account was given the same access as theirs, so I test what they test.
- **One tester could not sign up at first.** My own test accounts that day had used up the sign-up allowance for my home network, and the tester was on the same network. Cleared once found.
- Before sending, checked what happens to their data: **accounts are kept**. Nothing deletes an account on a timer, updates keep progress, and an account goes only when the family asks.

**The last production settings, and one outage.**
- Set the notification keys and my own alert address. The redeploy after them **took the whole site down**: every page failed, and a phone offered to download the page instead of showing it. The start-up check refuses to run with a malformed setting, as it was built to, and a pasted value was the likely cause. The site was back the same day.
- Decided the cost cap for the AI feature: prepaid credit with no automatic top-up is the cap for this round.

**A real Apple device, at last.**
- A borrowed iPhone: sound worked, and so did everything else checked. Typing an answer worked but felt awkward, which led to one of the fixes below.

**Three fixes from the first real use.**
- **The parent area could be opened from the learner sign-in screen** right after a parent signed in, because the password had just been typed. That screen now closes the parent area, and it asks for the password again. Adding a learner from that screen still asks only once.
- **An optional extra was always on screen and tied to nothing in particular.** It now appears only on a section the learner has already done well on, and uses that section's material. Simulated before the change: nothing in the tuning moved, so no number changed.
- **Typing answers on a phone.** The phone's own keyboard covered half the screen and lacked the symbols some answers need, so they were typed half there and half elsewhere. Touch screens now use one on-screen pad with everything on it; computers keep typing. Driven on a phone in two browser engines and on a computer.

**A job search that runs as an agent.**
- Set up a routine that I start by hand: it searches for roles that fit my resume, place and pay floor, checks each one against me requirement by requirement, plans how to close each gap with real work, finds the one person who decides on the role, drafts the notes, and puts it all in a tracker for me to read. It never applies, sends or signs in anywhere, and everything it writes about me comes from a fixed list of facts.
- It ran ten times today. A review of its setup found its tool access far wider than its job, so it was cut back to what the job needs: no access to my computer, my passwords or my files, and no outside apps. It also stops now when another run is already going, after two started at once.
- It keeps its resumes apart from mine: one general version for me to copy into my own resume by hand when it changes, and one version per role, kept only in its tracker. It never edits my resume or my facts.

**Verification and deployment.**
- One commit, pushed and live; two schema changes, confirmed applied in production. Production error log empty after the deploy.
- A signed-in check on the live site was refused by the sign-up rate limit, after several test accounts that day. That is the limit working; the three fixes are mine to confirm on my phone.
- Product document 0.77 to 0.79, technical document 0.58 to 0.59.

### Decided
- **Send to a parent and a learner now,** not only in-house, since their account is kept.
- **Prepaid credit, no automatic top-up,** as the AI feature's cost cap for testing.
- **Automatic dependency updates wait** until the testers have had a few days; a preview build of one shows errors by design, since previews have no database.
- **Simulate before changing anything tuned,** even when the change looks like layout.
- **Let an agent do the job search, never the applying.** It drafts and I send, after reading every draft.
- **The agent never touches my own resume.** It writes versions; I copy what I want.

### Noticed
- **A setting can take the whole site down.** The start-up check did its job, but the cost was every page at once. A value pasted by hand is the riskiest change of the day.
- **The first real person found what no script did.** All three fixes came from minutes of real use, after weeks of automated checks.
- **A password just typed is still a door left open.** The wall was right on paper; where the device is handed over mattered more than the clock.
- **My own testing got in a tester's way.** Test accounts made from my home network used up the sign-up allowance a tester on the same network needed. A live check had also run into that limit and looked like a pass.

## Numbers
- 937 automated tests across 102 files, all green
- Content checker green: 1,249 items, 3.75 million generated questions checked
- 1 commit, 28 files, +663 / −263 lines, 4 test files among them
- 2 schema changes, applied in production
- Product document 0.77 to 0.79, technical document 0.58 to 0.59

## Next
- Confirm the three fixes on my own phone.
- Each day: read what testers sent and what the record shows, and reply the same day.
- One question to each parent after the first session.
- The automatic dependency update, after the first few days of testing.
- Run the job agent once a day, and add a measured line about the testers to its facts once they have used it.
- Make test accounts from somewhere other than the network testers use.

## Current Status
- The prototype is in testers' hands. Everything is pushed and live, and the production error log is empty.
- Left for me: my own check of today's fixes, and listening.

## Key Reflections
- **Real use beats more checking.** Minutes on a real phone found what weeks of scripts had not.
- **Treat a production setting like code.** One pasted value took everything down; a setting deserves the same care as a commit.
- **Close the door where the handover happens.** Security that follows the clock missed the moment that mattered.
- **Measure before you move a tuned number, even by accident.** The simulation showed the change was safe before anyone had to find out.
- **Give an agent only the tools its job needs.** Rules say what it should not do; missing tools make sure it cannot.
- **Know what happens to people's data before you ask for it.** Checking that accounts are kept is what made it fine to send the link to a family.
