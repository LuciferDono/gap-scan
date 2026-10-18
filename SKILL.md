---
name: gap-scan
description: Separate startup gaps that are real companies from gaps that are features waiting to be cloned. Use when asked to find an unfilled gap, an untapped market, an edge case nobody solved, or "an idea I could build a startup around"; when generating or ranking candidate ideas; and equally for a SINGLE idea already on the table — "is this a company or a feature", "why isn't this just a Cursor/OpenAI/Google feature", "is this defensible", "is this already crowded", "who else is doing this", "should I build this". Applies the Barred test (is the best-positioned incumbent structurally conflicted from building it?) plus the Reach test (are the first 10-20 users nameable humans reachable today?), backed by parallel evidence legs that must name the nearest existing competitor for every gap claimed open. Skip for market research with no build decision attached, competitive analysis of an already-shipped product, and pricing questions.
---

# Gap Scan

Most "unfilled gap" lists are worthless because emptiness is not the same as opportunity. This skill kills weak candidates fast and forces the survivors to prove two independent things.

## The core test

**Two kinds of emptiness. Only one is a company.**

| Kind | Definition | Fate |
|---|---|---|
| **Temporarily empty** | Nobody got there yet | Absorbed into an incumbent's release note within ~two quarters |
| **Structurally unfillable** | The party best positioned to build it is *conflicted from building it* | Survives as an independent company |

Generator sentence for the second kind: *a gate that judges output is structurally compromised when it is the same model that produced it — so the incumbent cannot ship adversarial review against its own generation.* Generalise that shape. Four archetypes and worked examples: `references/structural-conflict.md`.

**The Barred test alone systematically mis-ranks.** Defensibility is orthogonal to whether anyone will use the thing in month one. A gap can be perfectly unfillable by incumbents *and* have no reachable first user — a real company you cannot start.

So every candidate is scored on both, and:

> ## HARD RULE — Reach is a mandatory field, not a consideration
>
> For every candidate, name the first 10–20 users as **actual identifiable humans or organisations reachable today**. Not a segment. Not a persona. Not a distribution strategy. If the answer is "developers who care about X," that is a failure to answer and the candidate scores Reach 1.
>
> This rule exists because it is the step that gets skipped. In the session this skill was built from, three independent strong-model agents optimised the defensibility axis and never checked reachability — with the rule sitting in their context the whole time. Defensibility rewards abstract argument; reachability requires naming people, so analysis drifts away from it. Do not let it.

## Workflow

### Phase 0 — Read what already exists
Read the project's own files before searching anything: prior briefs, portfolio notes, raw idea dumps, `CLAUDE.md`. The user's earlier words often contain the sharpest version of the thesis, and re-researching what is already on disk wastes budget.

Write down explicitly: **the deadline or decision point**, **who the founders are and what they have actually shipped**, and **any selection filter that applies** (accelerator thesis, investor mandate, competition rules) — or "none."

### Phase 1 — Generate candidates from the archetypes
Do not brainstorm freely. Walk the four archetypes in `references/structural-conflict.md` and ask for each: *what does this shape look like in the user's domain?* Aim for 10–15 raw candidates. Cheap to generate, cheap to kill.

### Phase 2 — Screen before spending research budget
Drop anything matching a known-saturated pattern in the domain before researching it. If a prior document in the project lists saturated categories, treat it as authoritative and cite it rather than re-verifying.

### Phase 3 — Evidence legs (churn tier)
Group survivors into 3–5 families; dispatch one parallel research agent per family. **Model economy is mandatory**: search, fetch, extract and dedup run at the cheap tier with low effort; synthesis, scoring and adversarial verification stay with the orchestrator or a strong model. An undifferentiated fleet of expensive agents is a defect.

Use the prompt template in `references/research-legs.md` near-verbatim — it enforces the output contract that makes results trustworthy, and it contains the evidence-hygiene rules that catch fabricated confidence.

**Persist each leg's raw output to `.scan/legN.md` in the project directory as it returns**, before synthesising. The final document cites these files; if they were never written, it cites nothing. Raw legs also survive a context compaction that the summary would not.

> **Evidence rule: every gap claimed open must name the nearest existing thing actually found, and why it does not cover the gap.** A gap with no named near-miss means the search was too shallow, not that the space is empty.

### Phase 4 — Score
Six axes — **Fit · Open · Barred · TTP · FMF · Reach**. Anchors and traps: `references/scoring-rubric.md`.

### Phase 5 — Converge
Invoke the `deliberate` skill to run the draft → audit → leverage loop against the ranked table. Do not reimplement it here; two copies drift.

**If `deliberate` is not available** (this skill travels; that one may not), run the loop inline as three *sequential* strong-model agents, each receiving the full context plus every prior agent's output verbatim: **Drafter** commits to one path and names its cost and its uncertainty — no hedging; **Auditor** is the friction and must name every drift it finds, "looks fine" being a failed audit; **Leverage** stress-tests the auditor's correction rather than rubber-stamping it, and ends with CONVERGED or NOT YET CONVERGED plus the single fact that would resolve it. Never skip this phase silently — a scan without a convergence pass is a ranked list, not a recommendation, and must say so.

Require the audit pass to check specifically for: self-refuting scores, cost-dishonesty (is the named cost the real one or the cheapest-sounding one?), constraint-washing, and locked-decision breaches.

### Phase 6 — Adversarial correction pass
**Convergence is not the end.** Before writing anything final, run the *Mis-scoring traps* checklist in `references/scoring-rubric.md` against the winner. In the originating session this pass caught three errors *after* the loop had converged, including one that would have doubled a headline statistic in front of an investor.

> **The rubric-drift rule.** The deliberation loop audits the *recommendation*, not the *rubric*. Any axis added, redefined or re-weighted **after** convergence has never faced adversarial review — and if it is the axis that picked the winner, that matters. Either re-run the audit, or state in the output that the axis is unreviewed.

### Phase 7 — Write the output
Use `assets/GAP_SCAN_TEMPLATE.md`. Write to the **current project directory** — project isolation applies; never write into another project's space.

Two sections get skipped under time pressure and are exactly what make the document trustworthy:
- **Rejected, with reasons** — nothing discarded silently
- **Verification gaps — do NOT build on these** — every unverified figure, secondary source and open question, named

### Phase 8 — Pitch interrogation (run on the winner; ideally on the top three)
A ranked table says *which* gap. It does not prove the gap can be **defended out loud**. Run the twelve questions in `references/pitch-interrogation.md` against the recommendation, in the founder's voice, before anyone writes an application or a deck:

the 50-character line · why this isn't a feature of `<named incumbent>` · what exists today and what specifically changes · why now, what became true in the last 18 months · who pays the first $10 *by name* · is the user the buyer · the world-after test · bottom-up path to $100M · why you · the pre-mortem · future resonance · wedge vs vision.

**An unanswerable question is a finding, not a research gap.** Write "no answer" and let it stand. Three of those and the candidate is not ready regardless of its score. Running the questions against the top *three* rather than only the winner is worth the extra time — the comparison exposes which idea is actually alive.

### Phase 9 — Capture
If the pass produced a genuine methodological insight rather than just a ranking, invoke `eureka` — or, if it is unavailable, write the insight to a dated file alongside the scan with the same structure: the argument arc, the falsifiable claims, and what would refute each. If the pass produced a decision the project must not forget, write a project memory. Neither is automatic.

## Single-candidate mode

When the user brings **one** idea and asks whether it is a company, skip Phases 1–2 and compress: one research leg for nearest competitors, then Barred + Reach + the mis-scoring checklist. The value is in two questions:

1. **Who is structurally barred from building this, and why?** No answer means it is a feature. Say so plainly.
2. **Name the first ten users.** If they cannot be named, it is not yet startable regardless of how good the idea is.

Then run the three killer questions from `references/pitch-interrogation.md` — #2 (why not a feature), #5 (who pays first, by name), #10 (what kills this). Those three catch the commonest failures: no mechanism, no reachable customer, no self-awareness.

## Output honesty rules

- **Score against the axis as written.** If an axis says "evidenced on disk," enthusiasm and intuition do not qualify. Score honestly, or change the definition *out loud*.
- **Never let the party that produced a recommendation score it.** Use a fresh agent with no authorship stake for any scoring pass over prior conclusions.
- **Report margins, not just winners.** A one-point lead over a three-way cluster is narrow. Say so rather than presenting it as decisive.
- **State surviving dissent; do not blend it away.** If one unresolved fact would change the call, name the fact and say the call should be re-run.
