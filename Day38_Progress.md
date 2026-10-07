# Day 38 Progress: Finding Testers, Reading Sessions, One More Check

## What I Did Today

### Study and Review
- Continued daily concept and vocabulary study, as always.

### Done

**Where free testers come from.**
- Asked whether testers can be found at no cost, since my group is small. The answer: nobody can recruit for me, but the sources are known, best first: my testers' own circles, parents who teach at home, local parents I can sit beside, and teachers I know, for a read of the content rather than for their students.
- **The sample is small for rates, not for finding problems.** Usability research finds that about five people surface most of the problems in a first session. What a small group cannot give is reliable rates, so the plan is several small rounds, each testing the fixes from the one before.

**Learning from young learners without interviewing them.**
- Young learners cannot say what confused them, and polite ones say it was fun. So the approach is to watch, not ask: one short question to each parent after the first session, and the product's own record for the rest.
- Built two reports for that, from data the product already keeps; **nothing new is collected:**
  - **Each session as a timeline:** every answer in order, how long each took, where help was asked, and how the session ended. A run of quick wrong answers, a pause before a stop, or a session that simply stops mid-way each read differently, the way they would to someone sitting beside the learner.
  - **Where learners struggle most,** by topic and by individual item. A topic missed evenly is hard; one item missed far more than its neighbours is a defect in that item, and the thing to fix.
- The timeline names learners, so it is kept apart from the report I can share.

**One more check, aimed at what had never been checked.**
- Nothing a tester sees had changed since the last full pass, and the production error log was empty.
- Every public page on a phone in two browser engines, light and dark: no errors, nothing off the side of the screen.
- **Tablets, for the first time:** the signed-in screens at three tablet sizes, upright and sideways, light and dark, in Safari's engine. Clean; I read the screenshots myself.
- **One scare that was my own test.** A sign-in problem appeared on tablets. Reproduced cleanly, the product behaved as designed; the test had copied one login into several browsers, which the security is meant to stop.
- **The AI feature was already running live** in production, so one decision on tomorrow's list was already made.

**My own phone.**
- Sound works, and typing answers works. I have no Apple device.

**Verification and deployment.**
- One commit, pushed and live.
- Product document 0.76 to 0.77, technical document 0.57 to 0.58.

### Decided
- **Several small rounds of testers, not one big one.** Round two tests round one's fixes.
- **Watch the learners; ask the parents one question.** No forms, nothing for a parent to track.
- **No background music.** It competes with thinking, and it is the first thing a parent mutes.
- **The Apple check goes to a tester or a shop's display device,** since I do not own one.

### Noticed
- **Fear asks for another check; the gaps ask for a different one.** Re-running the same sweep would have found nothing. Aiming at what had never been covered, tablets and the live settings, was the useful check.
- **A failing test can be the test's fault.** The tablet scare was mine. Reproducing it cleanly before touching the product saved a fix to something that was not broken.
- **The record already answers most of what I wanted from parents.** What it needed was a way to read it.
- **A missing setting can hide more than it seems.** The notification keys turn on my own alerts, not only a parent's; until they are set, I check by hand each day.

## Numbers
- 930 automated tests across 101 files, all green
- Content checker green: 1,249 items, 3.75 million generated questions checked
- 1 commit, 11 files, +389 / −8 lines
- Public pages: 9 pages, 2 browser engines, light and dark, no problems
- Tablets: 3 sizes, upright and sideways, light and dark, no problems
- Production error log: empty for the last three days

## Next
- Tomorrow: set the notification keys and my own alert address, redeploy, and confirm a spend limit on the AI feature.
- Make the first invite link and sign up through it once.
- The Apple check through a tester or a shop's display device: sound, typing, adding to the home screen. One line for the tester note: no sound on an iPhone usually means the silent switch.
- Send the first links to two or three people, then one question to each parent after the first session.

## Current Status
- Everything is pushed and live. The product has not changed for testers since the last full pass, and every check since has come back clean.
- Left for me, not the code: three settings, the first invite, and an Apple device in someone's hands.

## Key Reflections
- **Small groups find problems; they cannot measure rates.** Five people find most of what is wrong. Plan rounds, not a crowd.
- **Watch what young learners do; do not ask what they think.** The record of what happened is more honest than a polite answer.
- **Point checks at the gaps.** A check that covered the same ground twice proves nothing new; the tablet pass was worth more than another full sweep.
- **Reproduce before you fix.** The one scary result today was the test, not the product.
- **Less can be the design.** Leaving music out was a decision about attention, not a missing feature.
