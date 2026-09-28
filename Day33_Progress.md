# Day 33 Progress: Efficiency Pass, Third Security Review, Tester Round Prep

## What I Did Today

### Study and Review
- Continued daily concept and vocabulary study, as always.

### Done

**Efficiency pass.**
- The browser had been **downloading the whole learning-content library (178 KB compressed) on three screens** since the youngest year levels shipped. Fixed with a separate entry point and a test that **fails if any browser code reaches it again**.
- Database round trips per request roughly halved — one common request went from **23 statements to 11**.
- The build's own checks now run in about **a quarter of the time**.
- A dozen phone-size layout problems fixed by looking at every screen at 390 px.
- Documents 0.53 / 0.39, commit 48d8f29.

**Founder decisions on that pass's leftovers, all applied (0.54 / 0.40).**
- Post-session feedback now reflects **that session only**.
- One screen greys out unavailable choices instead of hiding them, and never skips itself.
- One suggested next step is highlighted instead of many.
- The not-found page sends a signed-in learner back into the product.
- Dashboard wording and phone layout settled.

**Third security review.**
- Two read-only reviews, then a fixing pass over every finding and over the day's new code.
- **Two promised rules were not true in the code and now are:** a learner signing in on a parent's device no longer inherits the parent's password window, and a learner holding the parent's cookie can change nothing.
- Parent password guessing is now slowed the way learner sign-in guessing already was (holds double within a day), and sign-up **refuses the ten thousand commonest passwords**.
- A pattern on a text field that could be made to run for minutes without an account is now a single scan, with a test.
- Also fixed: reset links, revocation notices, the device cookie, a not-found page that read the database for any cookie, a learner sign-in reset outside the password wall, a build that needed a secret to compile, the framework printing whole error objects, the AI feature's deny-list missing phone numbers, and the tests those controls lacked.

**Optional second sign-in step for parents.**
- Authenticator app support with recovery codes, a list of everywhere the account is signed in with sign-out buttons, a notice when an unfamiliar browser signs in, and a support switch.
- **Checked against the standard's published vectors.**

**Operational additions.**
- The product keeps its own error log, **scrubbed of anything typed**, read by an admin script.
- A script writes the weekly parent summary; the same summary appears as a "This week" card in the parent area.
- An optional advanced mode for learners who have finished a year level is now available, as the spec designed it — **its builder caught a bug that would have shipped**.
- All illustrations redrawn in **one consistent style**, still code-drawn, about three kilobytes more per screen.
- Notices to the parent's device through the browser's push service, **written from the standards with no dependency**; every message is one fixed line with nothing about a learner. Keys deliberately not set for the tester round.
- Direct notice to parents on the consent screen.
- A security contact at the standard address and a security policy in the repository.
- A review pack that writes each year level as one file for a tutor.
- A favicon.
- **An uptime check from GitHub every half hour, with no vendor.**

**Deployment.**
- Commits 33b044b, a9959fa, b71c582, c53d65b pushed and deployed.
- **Vercel's login wall removed from the production address.**
- Lighthouse on the live site: **99 performance and 100 accessibility, best practices and SEO on every public page**, 231 to 259 KB, **zero other hosts**.
- Verified before each commit: **782 tests**, lint, type checks, content checks, simulator, production build with leak check.

### Decided
- Notifications stay off for the tester round; testers report directly.
- The "QR code" is the authenticator step, scanned with any authenticator app; no store app exists or is planned.
- **Passkeys not built; awaiting a yes or no.**
- Uptime monitoring lives in GitHub, not a vendor.
- A session in the advanced mode is never cut short at a screen-time limit and never affects the learner's progress record; recorded as open decisions the founder can overrule.

### Noticed
- **The leak check must run after new files are staged.** It scans tracked files only, which let a key-shaped test fixture into a commit for an hour.
- **vercel.app addresses stay behind Vercel's login under "Standard Protection"**; only a custom domain is exempt, so the toggle had to go off.
- **Two test suites running on one database deleted each other's test accounts mid-test** and looked like flaky tests. A database lock now serialises runs.
- Five agents were cut off once by a session limit and resumed cleanly.

## Numbers
- 782 automated tests, all green
- Lighthouse: 99 performance, 100 accessibility/best practices/SEO
- Page weight: 231–259 KB, zero third-party hosts
- Common request: 23 → 11 database statements
- Content library download removed from three screens

## Next
- Decide whether the AI feature is live or canned for the round, with the spend limit set first if live.
- Ten minutes each of the two youngest year levels on a real tablet.
- Give yourself every year level, then send the tester note.
- Scan the authenticator code once with a real app.
- An expert read of one year level using the review pack.
- Restore drill on the database provider.
- Watch the uptime emails and the error log daily during the round.

## Current Status
- Product is live with a public address (no login wall) and strong Lighthouse scores.
- Third security review complete; two promised rules are now actually enforced in code.
- Optional authenticator-based second factor shipped and verified against standard vectors.
- Tester round is essentially pre-flighted, pending a few final checks.
- Notifications deliberately held back for the round.

## Key Reflections
- **A performance regression that ships quietly is worse than one that fails.** The content library was being downloaded on three screens for days — nobody saw it because nothing was broken. The fix included a test that fails if the browser code ever reaches it again, which turns an invisible regression into a loud one.
- **Promised rules must be verified in the code, not in the spec.** Two security rules were assumed true and were not. Reading the code against the promise is a different exercise from reading the code against itself.
- **Test infrastructure can lie.** Two suites deleting each other's accounts looked like flakiness, but was a real missing lock. Flaky tests deserve investigation, not reruns.
- **Leak checks must run against staged files.** Scanning only tracked files let a key-shaped fixture into a commit for an hour. The order of operations in a check matters as much as the check itself.
- **Writing security primitives from the standards beats adding a dependency.** The push notification system and the second factor were built from published specs with no third-party host, and both were verified against the standard's own vectors.
- **A vendor login wall can hide the product from the people you are sending it to.** Removing it is a one-toggle fix, but only if you check from a signed-out browser.
- **Not every decision needs to be made by the founder.** The advanced-mode session rules were recorded as open decisions the founder can overrule — writing them down as overridable is a way of moving forward without pretending certainty.
