# Day 28 Progress: BrickGenie Goes Live — First Real Play Session Finds Real Bugs

## Headline
The product went live, and the first real play session found five genuine bugs that testing had missed.

## What I Did Today

### Study and Review
- Continued daily concept and vocabulary study, as always.

### Shipped: Deployment to Production
- **Deployed to production.** The app is live on Vercel against the managed database, running in the same region as the data.
- Two deploy failures found and fixed along the way:
  1. An install flag the package manager no longer accepts.
  2. The game's tuning config was not being packaged into the deployed function, which made every request fail.

### Shipped: Security Audit and Fixes
- Reviewed every route against a checklist.
- Found and closed two routes that returned any family's child data to any signed-in parent.
- Also added:
  - A per-email sign-in hold
  - Re-authentication scoped to one device instead of all of them
  - A password change that signs out other devices
  - A security event log

### Shipped: Per-Request Access Control
- Access is now decided on **every request** by a single policy function using time, place, device, password age, and a session risk score — instead of being trusted after sign-in.
- A session that can't be the same person is ended.
- Anything without a policy is refused, and a route added without one fails the tests.

### Shipped: Guide Lockdown
- The guide previously accepted arbitrary text as a student message. Children only press buttons, so the server now refuses anything else.
- Added instructions for what to do if a child ever discloses being unsafe.

### Shipped: Public Pages
- Landing page, privacy, terms, accessibility statement, 404 and error pages, favicon, robots and sitemap, plus full browser security headers.
- Privacy and terms are honest drafts pending legal review.

### Shipped: The Visual Layer (Biggest Change)
The game was text and progress bars. Now:
- **Fights are drawn.** A right answer is a sword blow that lands; a wrong one is the enemy striking back. Damage numbers fly off.
- **The level list became a map:** a winding road of stops with a character who walks it. Tapping a level opens its history — medal, best run, times beaten.
- **The placement test became the child's first fight**, against an enemy of unknown strength that can't be lost. Every answer is a hit, so it still never tells a child they got something wrong.
- **Every item has an icon.**
- **Winning a level now ends in a pop-up with confetti.**

## Bugs Found by Playing, Not by Testing
This was the day's real lesson. The test suite was green throughout. Playing it found:
- **Correct answers marked wrong.** A money answer written with a dollar sign was rejected, the child was told they were wrong, and the enemy hit them. Same for numbers with commas, which the game itself displays. The reported "wrong accuracy" was the same bug: the arithmetic was right, the input wasn't.
- **The guide's "next step" button failed every time** against the real model. Every test used the offline stub, which accepted the malformed request.
- **The guide stayed on screen across questions**, so a child on question five saw advice about question two.
- **The check-in looked like it paid twice.** It didn't. A level's reward was displayed under the wrong heading.
- **A database setting** that was about to silently weaken the connection's security on a future upgrade.

## Numbers
- 376 automated tests, all passing
- Build clean, secret-leak check clean
- 13 commits

## Open for Tomorrow
- Fights on their own page, returning to the map
- A home screen separate from the map, with navigation menus (design still to be decided)
- Sound effects
- Real artwork to replace the placeholder characters
- Admin tasks: spending cap, uptime monitoring, test a database restore, legal review of the policy pages

## Current Status
- Product is live in production.
- Security audit complete with fixes shipped.
- Access control is now per-request, not per-session.
- Visual layer substantially upgraded.
- 376 tests passing, build and secret-leak checks clean.

## Next Steps
- Continue with the open items listed above.
- Get more testers. Real play found what the test suite could not.

## Key Reflections
- **Every bug today came from using the product, not from the tests.** This is the lesson worth carrying forward.
- A green test suite does not mean the product works. The offline stub accepted a malformed request that the real model rejected — the test was checking the stub, not the system.
- An input-validation bug can look like a correctness bug. The arithmetic was fine; the parser wasn't.
- More testers will be worth more than more test coverage. Testing confirms what you thought to check; play finds what you didn't.
- Shipping to production surfaces problems that no amount of local testing will, because the deployed environment is not the dev environment.
