# Day 32 Progress: Content Coverage Expanded, Multi-Level Profiles, Tester Pre-Flight

## What I Did Today

### Study and Review
- Continued daily concept and vocabulary study, as always.

### Done

**Content coverage expanded.**
- Three more year levels of learning content written, reviewed by independent readers, and shipped.
- Coverage went from **three year levels to six, with foundations beneath**.
- The youngest year levels are **illustrated**, so they can be used before a child can read. Every illustration is generated from data and checked automatically before release.

**Learner profiles now span year levels.**
- A family can move a learner between year levels **without setting up a new profile**. Everything the learner did comes with them.
- Year levels other than the free one need a subscription. Until payments exist, the founder grants one by hand through a script that **behaves exactly as the future billing integration will**.
- Each year level has its own visual identity, so moving up feels like arriving somewhere new.
- **Nothing a learner has earned is tied to a year level.**

**Audio is now opt-in.**
- Audio is something the learner turns on, not something that happens to them. Sound can be muted.

**Parent view.**
- Shows the curriculum code beside each topic that needs practice.

**Operations.**
- A **daily spending ceiling** was added for the AI feature, set under the provider's own limit.
- A **performance and privacy benchmark against nine competitors** was recorded in the internal documents: the lightest and fastest pages in the field, and the only ones loading nothing from third parties.

**Placement corrected.**
- Placement fixed for six year levels: a learner who already knows a year level's material now **starts at the next one, not at an unrelated early topic**.

**Tester documentation.**
- The tester note was rewritten: what testers need to know, what to do if something goes wrong, and a founder's checklist with every command a testing round needs.

**Deployment.**
- Production deployed and verified after each push.
- **Five commits**, all checks green: type checks, lint, 574 tests, the content checker, the tuning checks, the build and the secret-leak check.

### Decided
- One learner profile for a learner's whole time here; the year level moves with them.
- Nothing plays aloud until the learner asks.
- Year levels not yet written wait for **evidence from real use** before they are started.

### Noticed
- **Automated browser checks can drive the operating system's speech engine even when headless.** Every check now mutes it.
- **The generated hosting address sits behind the host's login wall.** The public address must be checked from a signed-out phone before anyone is sent a link.

## Numbers
- 574 automated tests, all green
- Content coverage: 3 → 6 year levels, with foundations beneath
- 5 commits, all checks green
- Competitor benchmark: 9 competitors compared

## Next
- Pre-flight for the first testers, from the author section of the tester note.
- Then send links to a small, hand-held group, and check the consent queue several times a day.

## Current Status
- Content coverage doubled again and now includes illustrated material for pre-readers.
- Learner profiles are portable across year levels; earned progress is never tied to a level.
- Audio is opt-in and fully mutable.
- Daily AI spending ceiling in place.
- Tester documentation rewritten and ready.
- Production deployed and verified.

## Key Reflections
- **A profile should belong to the learner, not the level.** Making progress portable across year levels removes a whole class of support problems and matches how families actually think about their child.
- **Grant access through the real path, even by hand.** The manual subscription script behaves exactly as the future billing integration will, so the access check is exercised for real from day one.
- **Placement should place, not punish.** A learner who already knows the material should land at the next thing, not be sent back to an unrelated early topic — that mistake looks like a bug to the family even when the logic is "correct".
- **Evidence before expansion.** Deciding that unwritten year levels wait for real usage signals is the right discipline; more content is not automatically better content.
- **Automation can trigger the OS itself.** A headless browser reaching the speech engine is the kind of side effect no one would catch by reading code. Muting in the harness and defaulting audio to off fixes both the test noise and the user surprise.
- **Verify the public address from outside the wall.** Anything gated by a hosting login will look fine to the author and broken to everyone else. A signed-out phone check is a one-minute step that prevents an embarrassing first impression.
