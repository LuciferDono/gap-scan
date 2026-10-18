# Scoring rubric

Contents: [The six axes](#the-six-axes) · [Anchors](#anchors) · [Mis-scoring traps](#mis-scoring-traps--run-this-as-a-checklist) · [Reading the table](#reading-the-table)

## The six axes

Score each 1–5. Total out of 30. **The total is a conversation-starter, not a verdict** — a candidate can win on points and still be unbuildable if it scores 1–2 on Barred or Reach.

| Axis | Question | Notes |
|---|---|---|
| **Fit** | Does this match the selection filter that actually applies? | An accelerator's stated thesis, an investor's mandate, a competition's rules. **If no filter applies, repurpose this axis as market timing** — why now rather than three years ago or three years hence — and say in the output that you did. |
| **Open** | How uncrowded is it? 5 = wide open | Scored from the evidence legs, never from intuition. Requires a named nearest-miss. |
| **Barred** | Who is structurally prevented from building this, and why? | See `structural-conflict.md`. Barred 2 is a rejection. |
| **TTP** | Time to credible progress — how much real movement is possible before the actual deadline? | If there is no deadline, score **time-to-first-real-user** instead and say so. |
| **FMF** | Founder-market fit **already evidenced** | Shipped artifacts, prior adoption, verifiable domain history. Not enthusiasm, not belief, not identity. |
| **Reach** | Are the first 10–20 users nameable humans reachable **today**? | Mandatory field. A segment is not an answer. |

## Anchors

**Open** — 5: no named player in the exact position, verified across multiple search framings · 3: adjacent players exist who could pivot in · 1: multiple funded direct competitors.

**TTP** — 5: something demonstrable and honest exists by the deadline · 3: a credible prototype plus a handful of users · 1: requires capital, licensing, or data that does not exist yet.

**FMF** — 5: shipped artifact with third-party adoption, directly on this surface · 3: shipped artifacts on an adjacent surface · 1: no evidence beyond interest.

**Reach** — 5: can name 20 specific people/orgs and has a reason each would reply · 3: can name a handful, the rest are cold · 1: cannot name anyone specific.

## Mis-scoring traps — run this as a checklist

Every trap below was committed in the originating session and caught only by an agent with no authorship stake. Assume you will commit them too.

### 1. Founder-fit inflated by thesis continuity
Crediting existing artifacts to a gap they do not actually sit on. In the originating case, two prompt-layer tools were scored as founder-market fit for a *substrate-layer* gap — the same instinct, a different layer, and therefore not evidence.

**Check:** name the artifact and the gap. Do they operate at the same layer, on the same surface, for the same user? If not, the score drops.

### 2. Founder-fit inflated by demographic advantage
A real, genuinely unfair advantage — language, geography, culture, industry background — scored on an axis explicitly defined as *evidenced on disk*. The advantage is real; it is not an artifact.

**Check:** either score it honestly against the axis as written, or redefine the axis **out loud** in the output. Never smuggle the redefinition in to rescue a preferred candidate.

### 3. Stars ≠ downloads ≠ installs ≠ users ≠ buyers
In the originating session, GitHub star counts of 11 + 8 + 8 became *"~30 people who installed"* inside a single reasoning chain, and that inflated number then justified the top Reach score. Stars are **awareness**. Downloads may be CI and mirrors. Installs may be one person on five machines.

**Check:** for every adoption number, state which of the five it is. Prefer the most conservative reading. Watch for a single spike inside a low baseline — that is a crawler, not demand.

### 4. First user ≠ buyer
Two different populations scored as one. The people reachable today (individual practitioners) are frequently **not** the people who would pay (procurement, platform teams, budget holders).

**Check:** name both populations separately. If they differ, the gap between them is a stated risk, not a rounding error. Either sell to the reachable one and show it has a payer, or admit the buyer is not yet reachable.

### 5. One finding stated as two
A percentage and its numerator quoted as separate evidence — "36.8% of skills flawed **and** 1,467 malicious payloads," when 1,467 *is* the flawed count and 1,467/3,984 *is* the 36.8%. Double-counts the claimed harm, and an informed reader will catch it.

**Check:** for every pair of statistics from one source, verify they are independent findings rather than the same finding twice.

### 6. Verifying the number but not the entity
Marking a statistic `[VERIFY]` while treating the platform, company or study it came from as established. If the entity turns out not to exist as described, the whole argument built on it collapses.

**Check:** verify the *noun* before the number. Does the platform exist, under that name, meaning what you think it means?

### 7. Self-scoring contamination
An analyst scoring its own prior conclusion inflates the founder-fit axis while the contradicting definition sits visible in the same document. Observed twice in one session.

**Check:** any scoring pass over prior conclusions goes to a fresh agent with no authorship stake. This is the single highest-value process rule here.

### 8. Rubric drift after convergence
An axis invented, redefined or re-weighted *after* the deliberation loop closed has never faced adversarial review — and in the originating session, that unreviewed axis is what picked the winner.

**Check:** re-run the audit against the changed rubric, or flag the axis as unreviewed in the output and discount it accordingly.

## Reading the table

- **Barred ≤ 2 or Reach ≤ 1 is disqualifying**, whatever the total. Move it to the rejected table with the reason.
- **Barred 5 + Reach 1–2** = a real company nobody can start yet. Note it as a future position or a data asset under another company; do not recommend building it now.
- **Barred 2–3 + Reach 4–5** = buildable, but the moat claim must be execution-and-accumulation, stated explicitly (see `structural-conflict.md`, final section).
- **Report the margin.** One point over a three-way cluster is a narrow lead. Say that. A tie is a tie — resolve it with a named tiebreaker rather than a decimal place.
