# Evidence legs — dispatch template and hygiene

Contents: [Design](#leg-design) · [The prompt template](#the-prompt-template) · [Why each clause](#why-each-clause-is-there) · [Evidence hygiene](#evidence-hygiene-applied-to-what-comes-back) · [Reading verdicts](#reading-crowding-verdicts)

## Leg design

Group candidates into **3–5 families of 2–4 related hypotheses each**. One agent per family, all dispatched in a single message so they run concurrently.

**Model economy is mandatory.** These legs are search, fetch, extract and dedup — throughput, not thought. Run them at the cheap tier with low effort. Synthesis, scoring and adversarial verification stay with the orchestrator or a strong model. An undifferentiated fleet of expensive agents is a defect, not a convenience.

Each leg needs its own family so results do not overlap; tell the agents nothing about each other.

## The prompt template

Use near-verbatim. The constraints are the point — each one prevents a specific failure.

```
You are a CHURN leg: web research only, no judgment, no recommendations. Today is <DATE>.
Use WebSearch/WebFetch aggressively.

Research these hypotheses and report what ALREADY EXISTS for each. For each, I need: named
companies/products/OSS projects/standards (with URLs), whether funded (accelerator batch or
VC round if known), what they actually do, and what they explicitly do NOT do.

H1. <hypothesis stated as a problem, not as a product idea>
    Search terms: "<term>", "<term>", "<term>", "<term>", "<term>"

H2. <...>
    Search terms: ...

H3. <...>
    Search terms: ...

Output format: one section per hypothesis; a table of NAMED PLAYERS
(name | url | funded? | what it does | what it does NOT cover); then a 3-line "how crowded"
verdict per hypothesis with a confidence label (HIGH/MED/LOW) reflecting how much primary
evidence you actually saw.

Do not editorialize or propose startup ideas. If you found nothing for a sub-area, write
"no named player found" explicitly rather than guessing or leaving it blank. Distinguish
model/product BUILDERS from EVALUATION or TOOLING players where both exist. Note explicitly
where a player serves the DEVELOPER building an app versus the END USER — that distinction
frequently separates a crowded category from an open one.

State your method at the end: which claims came from search snippets versus pages you
actually fetched, and which figures you did NOT verify against primary sources.
```

## Why each clause is there

| Clause | Failure it prevents |
|---|---|
| "no judgment, no recommendations" | Cheap-tier agents editorialising, which then gets mistaken for analysis upstream |
| "what it does NOT cover" | Competitor lists that make everything look crowded, with no read on the actual gap |
| Explicit search terms | Single-framing searches that miss the category under a different name |
| "no named player found" **explicitly** | Silence being read as emptiness. An unmentioned sub-area is ambiguous; an explicit null is data. |
| Confidence label per hypothesis | Uniform-sounding output where one section rests on ten sources and another on one |
| Builders vs. evaluators | The most common false-crowding error: a crowded builder space concealing an empty tooling space |
| Developer-user vs. end-user | The most common false-emptiness error, and its inverse — infrastructure-for-builders is often saturated while the same thing for the *person* is wide open |
| Method statement | Secondary-source figures arriving indistinguishable from verified ones |

## Evidence hygiene applied to what comes back

**Every gap claimed open must name the nearest existing thing.** No named near-miss means the search was too shallow, not that the space is empty. Send the leg back rather than accepting the null.

**Verify the noun before the number.** A statistic can be marked `[VERIFY]` while the platform, study or company it came from is silently treated as established. If that entity does not exist as described, everything built on it collapses. Check the entity first.

**One finding is not two.** A percentage and its numerator from the same study are one data point. Quoting both as separate evidence double-counts the harm and an informed reader will catch it.

**Funding figures are secondary until proven otherwise.** Search results disagree, conflate cumulative with round-specific, and go stale. Record them as "as reported by," never as fact.

**Accelerator batch membership is unreliable from aggregators.** Directory sites are frequently client-rendered and unscrapeable, so aggregators paraphrase and sometimes invent. Verify any company you intend to name in a written application against the accelerator's own pages.

**Vendor research has incentives.** A security vendor publishing a flaw-rate study, a lab publishing a benchmark of its own models, an evaluator paid by the evaluated — all usable, all cited with attribution, never presented as neutral fact. *A vendor grading its own product is itself evidence for the independence archetype; note it as such.*

**Date everything.** Market snapshots decay in months. Any market fact reused later needs a re-check date attached.

## Reading crowding verdicts

- **HIGH confidence + crowded** → reject immediately, cite the strongest named competitor, move on.
- **HIGH confidence + uncrowded** → the strongest possible signal, *provided* a named nearest-miss exists. If it does not, the leg searched one framing.
- **LOW confidence + uncrowded** → not evidence of a gap. Re-run with different search framings before scoring Open above 3.
- **Crowded on the surface, empty one layer down** → the highest-value result this method produces. Infrastructure-for-builders saturated while the same capability for the end user is untouched; model builders everywhere while independent evaluation is absent. **Look for this split deliberately in every family.**
