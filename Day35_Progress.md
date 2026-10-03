# Day 35 Progress: Visual Aids, Optional Hands-On Tool, Content Rewrite

## What I Did Today

### Study and Review
- Continued daily concept and vocabulary study, as always.

### Done

**Visual aids for the AI feature.**
- The AI feature now shows a **picture beside its explanations and refers to it in its words**.
- Pictures are **written ahead of time and checked automatically**; the AI never draws or invents one.
- Added several new picture types **modelled on what classrooms use**, plus larger, clearer labels on phones and a fix for pictures that were hard to read in the light theme.

**Pictures appear after a wrong answer, showing that exact item.**
- The explanation can point at something concrete.
- These **never appear before the learner has answered** and **never reveal the answer**.
- An **automated check enforces both rules**.

**Illustrated examples.**
- Every topic now has **at least one illustrated example**.

**Optional hands-on tool.**
- After a mistake, a learner can rebuild the idea with simple on-screen controls.
- Runs **entirely on the device**; nothing is graded and nothing is stored.

**Content rewrite.**
- Rewrote a large share of the learning content to be **more relatable to each age group**.
- Every change was checked by script to prove that **no number or answer moved**.

**AI feature changes.**
- Now **offered rather than opened automatically** after a mistake — the learner chooses whether to take it.
- Tightened its wording: finishes worked examples properly, doesn't give away the answer early, avoids hard-to-read punctuation.

**Verification and deployment.**
- Ran live checks on the deployed site with throwaway accounts across **three year levels**; all passed and the accounts were deleted afterwards.
- All work committed and pushed.
- **893 tests passing**, content checker passed every run.

### Decided
- **Help features stay optional and quick to leave.** Nothing should keep a learner away from their progress uninvited.
- **Skipped a further hands-on tool for older year levels** — low appeal, and the existing visuals already cover it.
- **Pictures must never print the answer**, in digits or in words.

### Noticed
- **Reviewers caught a number of wrong or misleading pictures before release.** Review stays a required step for content changes.
- **The AI occasionally works out a final step one turn early.** It reveals nothing new, but it's worth watching.

## Numbers
- 893 automated tests, all green
- Content checker passed every run
- Live verification across 3 year levels

## Next
- Watch two learners use it on their own devices.
- Have a teacher read the content.
- Optionally, measure how often the hands-on tool is used during the tester round.

## Current Status
- The AI feature is now offered, not automatic, and grounded in pre-written checked pictures rather than generated ones.
- Every topic has at least one illustrated example.
- A device-local hands-on tool is available after mistakes, with no grading or storage.
- Content rewritten for age-group relatability, with script-verified proof that no numbers or answers changed.
- Deployed, verified live across three year levels.

## Key Reflections
- **The AI must never draw or invent its own pictures.** Pre-written, automatically checked images keep the grounding honest and make wrong visuals catchable before release rather than after.
- **Pictures that show the exact missed item are for explaining, not for answering.** The rule that they never appear before an attempt and never reveal the answer is enforced by an automated check — not by convention.
- **A content rewrite must be provably inert where it counts.** Changing words is fine; changing numbers or answers is not. A script that proves nothing moved turns a risky edit into a safe one.
- **Reviewers still catch what automation doesn't.** Wrong or misleading pictures made it through checks and were caught by people — review stays a required step, not an optional one.
- **Optional help is worth more than automatic help.** The AI feature was opening itself after a mistake; making it a choice respects the learner and keeps the help from feeling like a consequence.
- **Not every idea needs to be built.** The older-year-level hands-on tool was cut on appeal and coverage grounds — a small, honest no is better than a low-value yes.
