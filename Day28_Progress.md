# Day 28 Progress: First Production Deploy + First Real Play Session

## Headline
First production deploy, then a play session that surfaced five real defects the test suite never saw.

## What I Did Today

### Study and Review
- Continued daily concept and vocabulary study, as always.

### Shipped: Live in Production
- Deployed to the hosting platform against the managed production database, co-located in one region.
- Two deploy failures found and fixed on the way:
  1. An install flag the package manager no longer accepts.
  2. A config file read at runtime that wasn't included in the deployed bundle — which made every request 500.

### Shipped: Security Audit and Fixes
- Reviewed every endpoint against a checklist.
- Found and closed two endpoints that returned another account's records to any authenticated user.
- Also added:
  - A per-identifier sign-in throttle
  - Re-authentication scoped to a single session instead of all of them
  - Credential changes that end other sessions
  - An append-only security event log

### Shipped: Per-Request Authorization
- Access is now decided on **every request** by a single policy function taking time, network origin, device, credential age and a computed session risk score — replacing a role granted once at sign-in and trusted thereafter.
- A session that can't plausibly be the same person is ended mid-flight.
- Anything with no matching policy is refused, and a new route added without one fails CI.

### Shipped: Locked Down a Model-Facing Endpoint
- It previously accepted arbitrary user text. The client only ever sends a fixed set of values, so the server now rejects anything else.

### Shipped: Public Site
- Landing page, privacy policy, terms, accessibility statement, 404 and error pages, icon, robots, sitemap, a health endpoint, and full browser security headers.
- Policy pages are honest drafts pending legal review.

### Shipped: Interface Overhaul (Largest Change)
- Replaced static text-and-progress-bar screens with an animated interactive layer.
- Navigable overview screen in place of a flat list.
- Per-item iconography.
- Modal completion state.
- All CSS animation, no asset pipeline yet; respects reduced-motion preferences and is hidden from screen readers where decorative.

## Defects Found by Using It, Not by Testing It
The day's real lesson. The suite was green the entire time. Hands-on use found:
- **Valid input rejected.** The parser accepted only a bare number, so formatting characters the app itself renders caused a correct submission to be scored as incorrect. A derived metric shown to the user was wrong for the same reason — the arithmetic was right, the input never was.
- **An external service call failed 100% of the time in production.** The request shape was malformed in a way the offline test double accepted and the live service refuses. Every test used the double.
- **A UI element persisted across steps** instead of being scoped to the step that raised it, so stale context followed the user forward.
- **A reward looked like it paid twice.** It didn't — one item was rendered under the wrong heading. The underlying records were correct, confirmed with tests.
- **A database connection setting** that was about to silently weaken on a future driver upgrade.

Each fix landed with a regression test.

## Numbers
- 376 automated tests, all green
- Build clean; secret-leak scan clean
- 13 commits

## Open for Tomorrow
- Move one flow onto its own route with a return path
- A separate home screen with navigation menus — design not yet decided
- Audio
- Artwork to replace placeholders
- Ops: spend cap, uptime monitoring, restore drill, legal review of the policy pages

## Current Status
- Product is live in production.
- Security audit complete, fixes shipped.
- Authorization is now per-request, not per-session.
- Interface overhauled with animation and navigation.
- 376 tests green, build and secret-leak checks clean.

## Next Steps
- Continue with the open items listed above.
- Get more hands-on users. Real use found what the test suite could not.

## Key Reflections
- **Every defect today came from using the product, not from the tests.** This is the lesson worth carrying forward.
- A green test suite does not mean the product works. The offline double accepted a malformed request that the live service rejected — the test was validating the double, not the system.
- An input-validation bug can look like a correctness bug. The arithmetic was fine; the parser wasn't.
- Shipping to production surfaces problems no amount of local testing will, because the deployed environment is not the dev environment.
- More users will be worth more than more test coverage. Coverage confirms what you thought to check; use finds what you didn't.
