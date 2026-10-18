# Structural conflict — the four archetypes

Contents: [What Barred measures](#what-barred-measures) · [The four archetypes](#the-four-archetypes) · [Generating candidates](#generating-candidates-from-the-archetypes) · [Scoring Barred](#scoring-barred-honestly) · [Weak-bar failure modes](#the-weak-bar-failure-modes) · [Worked examples](#worked-examples-dated) · [When Barred 3 is still buildable](#when-a-barred-3-is-still-worth-building)

## What Barred measures

Not *"has nobody built it?"* — that is the `Open` axis. Barred asks:

> **Who is best positioned to build this, and what specifically prevents them?**

The answer must name a party and a mechanism. "They haven't gotten around to it" is not a mechanism. "They are busy" is not a mechanism. A mechanism is something that would still stop them if they noticed the opportunity tomorrow and wanted it.

## The four archetypes

### 1. Neutrality — requires a cross-vendor position no single player can take
The product only works if it is trusted by parties who compete with each other. Any incumbent shipping it is shipping a thing whose value depends on not being them.

*Test:* would customers still trust this if the largest player in the category owned it? If no, the bar is real.

*Sub-case worth watching — the paid-by-the-evaluated conflict:* an evaluator funded by the party it evaluates has a structural conflict even when it is technically independent. That contrast case argues your position for you.

### 2. Adversarial to the generator — the tool indicts the output of whoever would ship it
A grader cannot credibly be the thing it grades. An incumbent shipping self-criticism is shipping a product whose success metric is its own failure rate.

*Test:* does the product's core function consist of finding fault with the incumbent's output? If yes, the bar is strong and durable.

### 3. Liability, not capability — no vendor ships the product documenting its own failures
The incumbent *could* build it trivially. Legal will not let them. Publishing a failure corpus, a drift ledger, an incident database or an underwriting product means creating discoverable evidence against yourself and inviting regulation.

*Test:* would this product's existence generate evidence usable against the incumbent in a dispute? If yes, they will never ship it no matter how easy it is.

*This is the strongest and most durable archetype — and usually the one with the worst Reach, because liability products sell to buyers who do not exist yet.*

### 4. Custody — requires holding data the incumbent may not, or will not, hold
Either regulation forbids it, or the incumbent's business model depends on *not* releasing it. Portability products live here: the data is the retention moat, so exporting it in a usable form means arming a competitor.

*Test:* does this require possessing or moving data whose confinement is the incumbent's moat? If yes, they will comply with the letter of any portability obligation and nothing more.

## Generating candidates from the archetypes

Do not brainstorm freely. For each archetype, ask the domain-specific question:

| Archetype | The question to ask of the domain |
|---|---|
| Neutrality | What here needs a referee, and why can no participant be it? |
| Adversarial | What here needs checking, and why can't the maker check it? |
| Liability | What here does everyone know and nobody will publish? |
| Custody | What here is locked in, and whose moat is the lock? |

Each question typically yields 2–5 candidates in any reasonably complex domain. That is the 10–15 raw candidates Phase 1 wants.

## Scoring Barred honestly

| Score | Meaning |
|---|---|
| **5** | Multiple independent mechanisms stack; no incumbent can ever ship it. Name each mechanism separately. |
| **4** | One strong mechanism, clearly stated, with no plausible workaround. |
| **3** | The natural incumbent is mildly conflicted, but adjacent well-resourced players are *not* barred and are already moving. The gap closes in quarters. |
| **2** | Nobody is meaningfully barred. Any incumbent adds this next sprint. This is a feature. |
| **1** | The incumbent is actively *advantaged* by shipping it. |

**Barred 2 is a rejection, not a low score.** Write it in the rejected table and move on.

## The weak-bar failure modes

**"Nobody has done it yet" dressed as a bar.** The most common error. If the reason is that nobody thought of it, the score is 2, however novel the idea feels.

**Conflating "hard" with "barred."** Difficulty is not conflict. A hard problem an incumbent wants to solve is a race, not a moat.

**Inventing a conflict to rescue a favourite.** If the mechanism takes a paragraph to explain and rests on a chain of assumptions, it is a 3 at best. Real bars state in one sentence.

**Missing that the winner will be a standard, not a startup.** When standards bodies plus multiple heavyweight incumbents are converging on a layer, the gap is real but it resolves into a protocol nobody owns. Barred can be 4 and the thing still not be a company. Check for this in identity, payments, interop and protocol layers specifically.

## Worked examples (dated)

> **These are illustrations of archetype shape, from a September 2026 AI/agentic-tooling scan. The market facts decay fast — reuse the reasoning, re-verify every fact.**
>
> **The scores below are the originating session's own, and were never scored by an independent party — which is exactly the contamination trap #7 warns about.** They are here as calibration anchors for what a 5, a 3 and a 2 look like, not as verdicts to inherit. If one of these candidates comes up in your own scan, score it fresh.

**Barred 5 — silent model-version drift detection.** The party with ground truth about the drift *is the party that caused it* (archetype 3: publishing "we changed behaviour under a stable alias" is a self-issued breach notice). Layered on archetype 1: no lab can grade a competitor credibly or itself honestly. Two independent mechanisms.

**Barred 5 — user-owned portable memory.** Memory is the retention moat, so exporting it in re-importable form arms the competitor (archetype 4 + 1). Portability regulation arguably requires it already; vendors satisfy the letter with flat dumps nobody else can ingest.

**Barred 5, unbuildable anyway — near-miss incident corpus.** Purest archetype 3: no vendor publishes its own failure corpus. But it is nonprofit-shaped, and its Reach is 1. *A perfect Barred with no Reach is the trap this whole method exists to catch.*

**Barred 3 — supply-chain gating for third-party agent extensions.** The registry operator is mildly conflicted (a gate that refuses installs fights ecosystem growth), but established security vendors are not barred at all and were already moving. Gap closing in quarters.

**Barred 2 — attention routing across agent fleets.** Genuinely unserved at the time; also something any orchestrator adds next sprint. Correctly rejected despite an empty field.

## When a Barred 3 is still worth building

A weak bar is not automatically fatal, and the originating session concluded exactly this against its own first draft:

> Defensibility does not only come from structural conflict. It also accrues from **coverage corpus** and **integration position** — both of which compound with time and neither of which an incumbent can buy instantly. Focused entrants routinely beat incumbents who are merely "already moving."

So a Barred 3 with Reach 4–5 can beat a Barred 5 with Reach 1–2. **But say which kind of moat you are claiming.** "Not a release note because structure forbids it" and "not a release note because we will out-execute and accumulate faster" are different arguments, and the second one is harder to make and must be made explicitly rather than by implication.
