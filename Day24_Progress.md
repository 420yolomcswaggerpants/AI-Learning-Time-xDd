# Day 24 Progress: Founder Pivot + Product Definition

## What I Did Today

### Study and Review
- Continued concept and vocabulary study (no code today).
- Focused on founder-relevant concepts: product definition, MVP scoping, AI product economics, competitive moats, retention mechanics.
- Studied pay and role trajectories across AI-adjacent paths (AI/ML Engineer, Product Manager, Forward Deployed Engineer, Solutions Architect, Founding Engineer, AI-Native PM, Agent Orchestrator) and made a deliberate decision to pursue the founder/builder path.

### Strategic Decision: Founder Path
- Decided to pivot from interview-prep focus toward building a product.
- Rationale: future roles are shifting, and the ability to prove something works and get someone to pay for it matters more than passing traditional coding screens.
- Recognized the capstone already proves capability to assemble working AI systems. Next step is applying that to a product aimed at real users.

### Product Work
- Selected a product direction in AI-integrated education: a game-based learning platform with an AI guide/tutor, where students progress by answering questions and where failure carries real in-game stakes without being punitive.
- Wrote and saved a comprehensive PRD (v0.25) covering all major product decisions.
- Wrote `docs/architecture.md` outlining system components and data flow.

### Key Decisions Made (meta-level)

**Business model and market**
- **Direct-to-consumer (B2C), sold to families.** Explicitly not selling to schools (crowded market, long cycles, poor fit for an entry-level product).
- **Parents are the buyer, students are the user.** Both must be won over.
- **Subscription with a free trial.** Paying never buys any in-game advantage.
- **Permanent ethical principle: no real-money purchases inside the game, no loot boxes, no gambling mechanics.** In-game currency is earned only by play, spent only on cosmetics, and never affects gameplay.
- **Relaunch/hard fail scenarios handled:** subscriptions that lapse retain all progress, just locked.

**Target user**
- **Grades 6–8 (ages 11–14), math first.** Middle school chosen because content has real prerequisite structure, students are independent enough to use it alone, and this is where math disengagement spikes.
- **COPPA is in scope for v1** (users under 13) — treated as a P0 compliance item, not deferred.
- **Science follows in Phase 2** (aligns to NGSS; math aligns to Common Core).

**Core mechanic (kept high-level here — full details in PRD)**
- The game is built on a **structured concept graph** with prerequisite relationships; every concept has a criticality score that influences routing and content weight.
- **Wrong answers carry stakes, but the student decides how to absorb them** — the design deliberately puts the player in the role of decision-maker rather than passive recipient of penalties.
- **The core balance rule is that a student at 70% weighted accuracy can beat any level**, verified through worst-case simulation. Challenging, not punishing.
- **Getting help is never punished.** Free guidance before and after answers; unlimited depth; no cost to mastery, no appearance as a negative on parent dashboards.
- **Rewards come from play and consistency, never money.** Nothing purchasable gives a gameplay advantage.

**AI guide design**
- The AI guide has a **defined teaching role with real constraints** (grounded to vetted curriculum, bounded scope, no free-form chat, silent during exams, escalation path for safety).
- The guide teaches; the consequences teach. These roles are kept separate by design.
- **Grounded generation only** — the guide must not invent factual claims, especially not to minors.

**Assessment and honesty**
- Mastery is measured by **accuracy thresholds, not just completion**. Medals require real performance.
- **Cumulative exams** test retention across everything learned, with stricter rules than normal play.
- **Placement test** personalizes the starting point.
- **Honest-play signals** discourage cheating gently (no leaderboards, no purchasable advantage, so cheating gains nothing).

**Parent experience**
- Parent dashboard and email notifications, with per-category controls. Billing and safety notices are always on.
- **Optional screen-time controls**, off by default, that never cut off a fight and never cost progress.
- Parents control their child's data (view, download, delete).

**Content production**
- Original content drafted with AI, verified automatically, reviewed by founder, expert review once funded.
- **Openly licensed references only** (avoiding non-commercial licenses since this is a paid product).
- No rewording of textbook questions.

**Phasing**
- **Phase 1: Solo proof of concept** to show investors and validate student behavior. Narrow scope: one subject, one grade, ~30 concepts.
- **Phase 2: Family beta** with expanded scope, parent app, real subscriptions, and COPPA consent flow.
- **Phase 3: v1 launch** after investment — team, full compliance, payments, scaled content.

### Design Principles That Guided the PRD
- **Help must never feel like failure.** This shaped the entire help and consequence system.
- **Consistency and accuracy matter equally.** Rewards split roughly evenly between daily logins and level performance.
- **Stakes without shame.** Failure is framed as in-game consequence, never as judgment of the player.
- **Mastery is earned, never bought.** No real-money path to progress or advantage.
- **The guide teaches; the consequences teach.** Roles are strictly separated.
- **Compliance is P0, not deferred.** COPPA and child safety are not "later" problems.

## Current Status
- Capstone remains complete, annotated, optimized, and pushed.
- New product direction defined and documented (PRD v0.25 + architecture).
- Founder path chosen; coding-gap concern reframed as a founder concern rather than an interview concern.
- No prototype code written yet.

## Next Steps
- Begin building the prototype (single-session MVP: one concept cluster, core loop, one tutor intervention, no persistence).
- Validate the hardest technical problems first: content verification and the AI guide's bounded behavior.
- Test with real students from families the founder already knows.

## Key Reflections
- The capstone is a strong proof of concept and does not need further polishing—its job was to prove capability, and it did.
- Building a product is a different game than building a portfolio project. The hard part is not the code; it is finding a problem someone will pay to solve.
- The riskiest design decision in this product is the consequence mechanic. Get the framing wrong and the product fails on anxiety, not on features.
- One polished, shippable product matters more than more tutorial-level projects.
- The PRD itself is a meaningful artifact — it forced dozens of decisions that would have otherwise been made ad hoc during build, and it documents the ethical principles that will matter to parents and investors.
