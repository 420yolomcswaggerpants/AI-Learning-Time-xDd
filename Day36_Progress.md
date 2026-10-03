# Day 36 Progress: Playtest Fixes, Research Pass, Invite Links

## What I Did Today

### Study and Review
- Continued daily concept and vocabulary study, as always.

### Done

**Code pass first.**
- Looked for performance and line-count savings before anything else. The code was **already well tuned** from the earlier efficiency pass; the only safe trim was two functions nothing used. No speed-up claimed, because nothing was measured.

**Playtest through a child's eyes and a parent's.**
- Scripted playtests on a phone-sized screen as **four kinds of learner** (one who can barely read, one struggling and losing, an older one who spots anything babyish, an impatient one who double-taps, reloads and leaves midway) and as **one parent** going from the front page to the dashboard.
- Each finding was sorted into a **clear defect** (fixed) or a **judgement call** (brought to me as a question, with the research behind it, and decided one by one).
- Fixed: a number that **read zero before it should have**; placement and an unfinished session now **carry on where they stopped** after a reload or Back; repeat attempts no longer open the same way every time; **every family had been on New York time**, so sign-up now records the parent's own time zone, with a setting in the parent area that applies from the family's next midnight; account deletion now says it worked; icons on the main buttons for the youngest; one on-screen choice now reads **in words, with the numbers behind a tap**; a piece of feedback that showed twice shows once; an icon redrawn so it reads as what it is; the AI feature's offer moved higher on short phones.
- **One rule change for the youngest year levels**, made gentler, chosen from three simulated options. Older learners no longer see wording written for small children.
- The front page now answers the three things a careful parent asks first, one line each.

**Research pass before handing it to unpaid testers.**
- Read what is known about first sessions and friends-and-family testing: education apps keep roughly **one in seven new users past the first day and one in fifty past a month**; feedback asked for inside the app gets **many times the response of email**; unpaid testers need a deadline, a reply, and to be told what changed because of them.
- Built from it:
  - **Invite links.** One link per group of people I know. An account made through one needs nothing opened by hand, and its learners can start at once. Links have **no expiry and no cap by default**; I revoke a link when a round ends.
  - **A feedback button on every screen's menu.** A grown-up writes a few lines; a child picks from a fixed list and **types nothing**. Where they were is attached. A script reads the notes and says what is new.
  - **Errors thrown in a tester's browser are recorded** beside the server's own; before, a tablet failing on a button was invisible.
  - **A funnel, printed first in the metrics:** where new families got to and how long each step took.
  - **Two notices:** my own device is told when something arrives that I handle by hand, and a parent can ask to be told when it is done, so the tab need not stay open.
  - **The tester note rewritten:** ten lines to do, word asked for within two days, and a template for writing back about what changed because of them.
- **Six wording fixes** in the first items a tester meets, from a read of 346 of them; no answer moved.
- **Placement is shorter for the youngest year levels**, from a simulation of 2,000 runs per kind of child.

**Safari, without an Apple device.**
- Ran the site under Safari's browser engine on a simulated iPhone. **One defect:** some on-screen buttons did nothing on a tap there, so one kind of input could not be given. Fixed, and verified on a bare page in that engine. Buttons no longer wait for a possible double-tap on touch, and one screen is tighter on a short phone.
- A real iPhone and iPad are still unverified: sound, read-aloud, the soft keyboard, home-screen install and notifications.

**Verification and deployment.**
- Four commits, all pushed, with three schema changes among them; the live site checked after the third push, and the fourth deploy was still finishing as I stopped.
- Product document 0.68 to 0.71, technical document 0.54 to 0.56.

### Decided
- **Invite links instead of hand-made tester accounts**, so nobody's account is managed by hand. **No time limit on them**: this is in-house testing, and I revoke by hand.
- **Rejected two suggestions** after thinking about who actually uses this: an Undo after a settings change (unticking the box is the undo) and hiding Sign out behind a grown-ups menu (the older learners already know the family's sign-in, and it cost every parent a tap).
- An interrupted session **resumes rather than restarts**.
- The youngest get **icons on the main buttons only**, not everywhere.
- That on-screen choice reads in words, same choice underneath.
- Time zone: build it, applying from the next day, not mid-day.
- The youngest year levels: the gentler of the simulated rules.

### Noticed
- **Simulated testers find defects; they cannot say whether a child wants to come back.** Only real families can, and the whole day was about being ready for them.
- **Written reasons protected earlier decisions.** Two things a playtester flagged were deliberate, and the comment beside each said why; nothing was undone by accident.
- **Safari's engine and Chrome's disagree on a cancelled touch event.** Nobody on a desktop could have seen that defect.
- **Limits are a cost.** An expiry and a cap on invite links were one more thing to manage; for a round among people I know, none plus a revoke is simpler.

## Numbers
- 922 automated tests across 100 files, all green
- Content checker green: 1,249 items, 3.75 million generated questions checked
- 4 commits, 88 files, +2,845 / −331 lines, 11 test files among them
- 3 schema changes
- 346 opening items read, 6 reworded
- Research: ~14–15% day-one and ~2% day-thirty retention for education apps; in-app feedback answered by 30–40% versus under 5% by email

## Next
- Set the two remaining production settings (my own alert address, the notification keys) and redeploy.
- Make the first invite link against production and sign up through it once.
- Ten minutes each on a real iPhone and iPad, sound on.
- Send the first links. Reply to every note within two days, and post what changed because of them.
- Still open from before: have a teacher read the content; watch two learners on their own devices.

## Current Status
- The prototype is ready for unpaid testers: invite links, feedback from inside the app, browser errors captured, a funnel in the metrics, two notices, and a rewritten tester note.
- Live, with the latest deploy finishing as I stopped.
- Left for me, not the code: two production settings, the first production invite, and a pass on real Apple devices.

## Key Reflections
- **We get one shot with unpaid testers.** Paid testers come back after a bad first session; friends do not. The first ten minutes, the feedback button in the menu, and a reply within two days are the product this week.
- **Read before building.** One evening of research changed what got built: invite links instead of accounts, feedback inside the app instead of email, a funnel instead of a feeling.
- **Think about who is actually using it.** Two reasonable-looking suggestions died once I pictured the oldest learners and a tired parent. Protection that protects nothing is friction.
- **Simulate the device you cannot buy.** Safari's engine on a simulated phone found a real defect; it still does not replace ten minutes with the real thing, and the note says so.
- **A limit is something to manage.** Open-ended links plus a revoke beat expiries and caps for a round among people I know.
- **Written reasons are cheap insurance.** A comment beside a deliberate choice kept it from being undone by the next pass.
