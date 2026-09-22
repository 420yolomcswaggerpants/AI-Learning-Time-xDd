# Day 29 Progress: Quality Day — Audit the Corpus, Not Just the App

## Headline
A day of quality work, and the most valuable hour was spent on a script rather than on the app.

## What I Did Today

### Study and Review
- Continued daily concept and vocabulary study, as always.

### Shipped (8 commits, all pushed)
- **70 files changed, ~4,300 lines added.**
- **Test suite: 379 → 411, all green.** Build and secret-leak scan clean throughout.

### Main Screen Restructured
- It had grown into one long scroll with two competing primary actions. Now there's one, and everything else lives behind modal windows opened from a top strip: the daily reward, the inventory, and a pre-action setup window. (This will be changed)
- The daily reward got an animated reveal instead of a line of text.
- It now states exactly when the next reward is available, computed from a real timezone-aware clock rather than "tomorrow" — correct on the two days a year when adding 24 hours is wrong.

### Account Recovery (Didn't Exist Before)
- There was **no way past a forgotten password**.
- The system still can't send email, so rather than fake it: the request goes to an operator queue with no token attached, and an admin command issues a one-hour single-use link after the operator verifies the requester through a channel they already had.
- The form answers identically for addresses that don't exist, so it can't be used to find out who has an account.
- Using a link ends every session on the account.

### Adjacent Hole Found and Closed
- The only way to change a sub-profile's credentials was a "replace this profile" action that transfers the slot to a different person and **discards everything the old one had accumulated**.
- Someone whose sub-profile forgot a 4-digit code would have reached for the only button there was.
- That's now its own operation that changes nothing else and clears the associated lockout.

### Assistance Feature Fixed
- Its "next step" control could be pressed indefinitely — the external service kept inventing steps past the end of the material, and enough presses hit a conversation cap and failed outright.
- Now bounded by the actual length of the material and ends cleanly.
- The same feature was telling users to attempt the next step themselves while giving them no way to; it now offers a real interactive attempt.
- **Declined to add a free-text input**, despite it being requested. It's the one place someone could disclose something requiring escalation, and the review queue and notification that must ship alongside depend on email. Deferred with the reasoning written down.

## The Day's Real Lesson: Audit the Corpus, Not Just the App
Yesterday every bug came from playing the product. Today the most valuable finding came from a script that swept **all 87,000 generated content items** — a class of defect nobody would hit often enough to notice by hand:

- **52% of multiple-choice items contained a throwaway option** that could be ruled out on sight, making a four-option item effectively a three-option one. Cause: every one of the 145 content templates declared exactly enough plausible alternatives and never one spare, so any collision became filler. Authored an additional one for all 145. **Now 12%.**
- Some items presented **negative values as options** in a context where the audience has never encountered them — reads as a typo, not a choice.
- **Rounding-type items offered options that weren't valid outputs** of the operation being asked for.
- A parameter draw could produce a **degenerate item** where every meaningful alternative fell out of range.
- And one rule added in the morning was **too aggressive**, which was itself causing one of the above.
- Separately, and reported directly: a family of items could be **completed without doing the underlying work** — the information needed was restated in the prompt. Rewrote them, and made **"an item may never contain its own solution"** a rule the build enforces. Sweeping the corpus with it caught two more instances nobody had noticed.

### Two Upgrade Options Were Actually the Same Option
- Measured on the real engine, they were **identical on the first selection and 2.4% apart on the third** — and a typical session offers about six.
- Worse, one of them scaled off a value that **shrinks when things are going badly**, so it paid least to whoever was struggling.
- Couldn't be tuned out; replaced and re-simulated across **4,000 runs per case**.

## An Hour Lost, Worth Recording
- Several "bugs" reported this morning were **already fixed and committed** — the live deployment was serving an older build.
- **Before debugging anything reported from production, check which commit is actually deployed.** Cost about an hour.

## Numbers
- 8 commits, all pushed
- 70 files, ~4,300 lines added
- Test suite: 379 → 411, all green
- Build clean; secret-leak scan clean
- Corpus swept: 87,000 generated content items
- Filler-option rate: 52% → 12%
- Upgrade option re-simulation: 4,000 runs per case

## Open for Tomorrow
- One flow still needs its own route with a return path
- A separate landing screen with navigation — design undecided
- Audio, and final artwork
- One documented section of the spec is now stale and needs re-simulating (flagged in place rather than rewritten with invented numbers)
- Four placeholder content items still waiting on artwork
- Admin: spend cap, uptime monitoring, restore drill, legal review

## Current Status
- Product live in production with 411 tests green.
- Main screen restructured; account recovery now exists; sub-profile credential change is a safe operation.
- Assistance feature bounded and no longer able to loop or fail outright.
- Content corpus audited and substantially improved.
- One stale spec section flagged for re-simulation rather than papered over.

## Next Steps
- Continue with the open items listed above.
- Keep sweeping the corpus with automated rules — it found defects no hand-testing would.
- Always confirm the deployed commit before debugging a reported issue.

## Key Reflections
- **The most valuable hour today was spent on a script, not the app.** Auditing the corpus found a defect class affecting half of all multiple-choice items — something no amount of manual play would have surfaced.
- **Content bugs scale with the corpus.** One bad template rule multiplied across 87,000 items. Rules must be enforced at build time, not reviewed by hand.
- **Two options that look different can be the same option.** Measuring on the real engine, not the spec, revealed it. And a choice that pays least to the struggling player is worse than a weak choice — it's an unfair one.
- **Check what's actually deployed before debugging.** An hour lost to investigating already-fixed issues is an hour the deploy check would have saved.
- **Declining a feature with written reasoning is a decision, not a delay.** The free-text input was deferred for a specific, documented reason tied to safety infrastructure that isn't ready.
- **When a spec section goes stale, flag it — don't invent numbers to fill it.** Honest gaps beat fabricated precision.
