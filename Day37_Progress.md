# Day 37 Progress: Parent Area, Family Clocks, Final Pass Before Testers

## What I Did Today

### Study and Review
- Continued daily concept and vocabulary study, as always.

### Done

**The parent area, named for who it is for.**
- An adult tester said they **could not get to the parent portion**. It was right there, under a word that meant nothing to them. The area is now called the plain word a parent would look for, marked with a **padlock**, and reached by that name from every screen; the sign-in for learners is named for them too. A code on top was considered and rejected (below).
- Sign-up, the help text and the error wording all point to the area by its new name, and nothing anywhere points to the old one.

**Every family on its own clock.**
- Day 36's fix recorded a time zone at sign-up; every account from before it, **including my own, was still on one city's clock**. An account whose zone nobody has chosen now adopts the parent's device zone the first time a parent signs in.
- A parent whose device is on a different clock from the family's is **asked, not moved**: switch from the next midnight, or keep. Keeping is remembered for that trip and asked again once either clock changes. The zones the testers are in are listed first.

**The tester note, served by the site.**
- The note for testers is now **a page on the site**, built from the same file I send, so the two cannot drift; my own half of the file is never shown. A test proves every line of the tester half appears and nothing of my half does.
- The note was reworded in 21 places to **say what the screens say**.

**A picture for the youngest learners.**
- One picture was **hard to take in at a glance**; I noticed it myself while using it. Laid out again, from research on how young children take in a picture, and it reads at a glance now.

**One last full pass before any human sees it.**
- **Code and the live site:** every public page measured by Lighthouse at 99/100/100/100, about 240 KB, nothing loaded from a third party. A scripted visual sweep on a phone, dark and light, and on a desktop: nothing overflowed, no errors. A scripted run through the live site end to end as a parent and as a learner, from the front page to deleting the account, with no errors; it found the tester page missing (fixed) and the notification keys still unset (mine to do). The production error log is empty for three days.
- **Learning content:** a teacher-style read of 3,240 generated items. **No wrong answers.** One class of item could offer an option that its own wording ruled out; fixed where items are generated, and the checker now refuses any item of that class, so it cannot come back. A few wording fixes beside it: a spoken comma, a plural, an item that gave away its own answer.
- **The AI feature:** driven on the real model as three learners, from the youngest, middle and oldest year levels, and every reply read. Each names the mistake, speaks at the learner's level, and teaches rather than tells.
- **Wording:** a proofread of everything a parent or learner reads. **56 fixes**, mostly the renamed area, plainer error messages, and one number typed by hand where a setting should have been read.
- **One test failed only on Mondays**, because a week is one day long on its first day. Fixed to hold on every day of the week.

**Verification and deployment.**
- Five commits, all pushed, one schema change among them; the live site checked after the last deploy.
- Product document 0.71 to 0.76, technical document 0.56 to 0.57.

### Decided
- **A plain name and a padlock, not a code.** The area already asks for the password; a code would cost every parent a step and protect nothing the password does not. The older learners already use the family's sign-in.
- **An account that never chose its clock follows the parent's device.** A travelling parent is asked, never moved; a switch starts at midnight, never mid-day.
- **Feedback from four testers comes to me directly.** They are all people I know; I did not add another feedback prompt inside a session.
- **Nothing more to build before the first testers.** Each pass finds less than the one before; what is left can only be learned from real people. The tester note's own list is tomorrow; today, at most, I try it on my phone.

### Noticed
- **A fix at sign-up is not a fix for anyone who signed up earlier.** Day 36's clock fix did not reach my own account.
- **The word on the tab was the defect.** The parent area worked; nobody could find it.
- **Each pass finds less than the last.** The first readiness pass found a missing page and unset keys; this one found wording and one class of item. The falling yield says the remaining unknowns are not in the code.
- **The checker proves answers; it could not see an option the wording ruled out.** A human read found it; now the checker sees that class too.
- **I found the picture defect by using it, not by a script.** The next step, me on my own phone, is the same thing at full size.

## Numbers
- 928 automated tests across 101 files, all green
- Content checker green: 1,249 items, 3.75 million generated questions checked
- 5 commits, 64 files, +921 / −190 lines, 5 test files among them
- 1 schema change
- Live site: 99/100/100/100 on every public page, about 240 KB, no third-party hosts
- 3,240 generated items read; 56 wording fixes in the product, 21 in the tester note
- Product document 0.71 to 0.76, technical document 0.56 to 0.57

## Next
- Tomorrow: the tester note's own list. Set the two remaining production settings (my own alert address, the notification keys), redeploy, and decide whether the AI feature runs live or canned for this round.
- Make the first invite link against production and sign up through it once.
- Ten minutes each on a real iPhone and iPad, sound on; possibly my phone today.
- Send the first links to two or three people. Reply to every note within two days, and post what changed because of them.
- Still open from before: watch two learners on their own devices.

## Current Status
- Everything is pushed and live; the last deploy serves the tester page.
- Nothing left to build before testers. What is left is mine to do, not the code's: two production settings, the first invite, a pass on real Apple devices.
- Tester one is me, on my own phone, with nobody else watching.

## Key Reflections
- **Call things what the person looking for them calls them.** The tab was named for what it showed, not for who it was for, and a tester walked past it. A rename and a padlock was the whole fix.
- **Checks have a falling yield.** When a full pass finds only wording, the next defect is cheaper for a tester to find than for me. That is the signal to stop checking and start watching.
- **A fix for new accounts leaves the old ones.** Everyone from before the fix, me included, kept the old behaviour. Think about the rows that already exist, every time.
- **Ask; do not move.** A device on another clock may be a holiday. A setting that changes itself under a parent is worse than one that asks.
- **Use it yourself first.** The one defect no script flagged, I found by using it. The first tester is me, and nobody else sees that round.
- **Fear is not a finding.** Being scared before the first outside eyes is not evidence that something is missing. The list of what is left is short, and all of it is mine.
