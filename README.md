# gap-scan

**[English](./README.md)** · [简体中文](./docs/readme/README_zh-CN.md) · [日本語](./docs/readme/README_ja.md) · [한국어](./docs/readme/README_ko.md) · [Español](./docs/readme/README_es.md) · [Deutsch](./docs/readme/README_de.md) · [Português (Brasil)](./docs/readme/README_pt-BR.md)

A portable prompt-skill that separates startup gaps that are real companies from gaps that are features waiting to be cloned. Works across Claude Code, Cursor, Codex CLI, GitHub Copilot, Antigravity, and any system-prompt LLM.

> Part of the **[LuciferDono skills](https://github.com/LuciferDono/skills-stack)** collection: minimal, portable, agent-agnostic skills that fix one real failure mode each.

## The problem

Most LLM "startup idea validators" tell you your idea is great. The ones that disagree hand you a generic PESTEL analysis. Neither answers the two questions that actually matter.

**Question 1 (the Barred test):** Is the best-positioned incumbent structurally conflicted from building this? If OpenAI, Cursor, Google, or Microsoft can ship your idea as a weekend feature, you don't have a company. You have a feature waiting to be absorbed.

**Question 2 (the Reach test):** Are the first 10-20 users nameable humans reachable today? If you can't name them with first-and-last names and a channel to reach them, you don't have a market. You have a hypothesis.

Fail either test and the idea is not a company, no matter how large the TAM slide claims.

## What it does

When you present a startup idea (or ask gap-scan to generate candidates), it runs both tests in parallel:

1. **Barred test:** who's the best-positioned incumbent to build this? What would they have to sacrifice to ship it? If the sacrifice is cheap, the gap is a feature waiting to be cloned.
2. **Reach test:** list 10-20 concrete first users by name/role/company. Which channel reaches them today? If this collapses to "developers on Twitter" or "any SMB owner," the Reach test fails.

Both tests run against **evidence legs** (parallel research passes) that must name the nearest existing competitor for every gap claimed open. No "no one is doing this" without a receipt.

Output ends with one of three verdicts:

- **COMPANY**: passes both tests. Here's the first-10-users list, the Barred argument, the structural conflict that protects you.
- **FEATURE**: fails the Barred test. Name the incumbent likely to absorb this, and the timeline.
- **HYPOTHESIS**: fails the Reach test. Name the research gap: who do you need to interview before this becomes a company.

## Install

gap-scan ships as platform-specific wrappers under [`dist/`](dist/). Pick your agent:

| Agent | Install path | Per-agent docs |
|-------|-------------|----------------|
| **Claude Code** | `~/.claude/skills/gap-scan/` | [`dist/claude-code/`](dist/claude-code/) |
| **Cursor** | `.cursor/rules/gap-scan.mdc` | [`dist/cursor/`](dist/cursor/) |
| **OpenAI Codex CLI** | `~/.codex/AGENTS.md` or `./AGENTS.md` | [`dist/codex/`](dist/codex/) |
| **GitHub Copilot** | `.github/copilot-instructions.md` | [`dist/copilot/`](dist/copilot/) |
| **Google Antigravity** | `~/.antigravity/agents/` (format evolving) | [`dist/antigravity/`](dist/antigravity/) |
| **Any system-prompt LLM** | paste into system-prompt field | [`dist/generic-system-prompt/`](dist/generic-system-prompt/) |

### Claude Code (quickest)

```bash
git clone https://github.com/LuciferDono/gap-scan ~/.claude/skills/gap-scan
```

Windows:

```powershell
git clone https://github.com/LuciferDono/gap-scan "$env:USERPROFILE\.claude\skills\gap-scan"
```

### Cursor (per-project)

```bash
mkdir -p .cursor/rules && curl -fsSL https://raw.githubusercontent.com/LuciferDono/gap-scan/main/dist/cursor/gap-scan.mdc -o .cursor/rules/gap-scan.mdc
```

### Codex CLI

```bash
mkdir -p ~/.codex && curl -fsSL https://raw.githubusercontent.com/LuciferDono/gap-scan/main/dist/codex/AGENTS.md -o ~/.codex/AGENTS.md
```

### GitHub Copilot (per-repo)

```bash
mkdir -p .github && curl -fsSL https://raw.githubusercontent.com/LuciferDono/gap-scan/main/dist/copilot/copilot-instructions.md -o .github/copilot-instructions.md
```

### Anything else

Paste [`dist/generic-system-prompt/system-prompt.md`](dist/generic-system-prompt/system-prompt.md) into your model's system-prompt field.

## Trigger phrases

| You say | What fires |
|---------|-----------|
| "find an unfilled gap" | Candidate generation + both tests on each |
| "untapped market for X" | Barred + Reach on X |
| "is this a company or a feature?" | Barred test only (single idea) |
| "why isn't this just a Cursor/OpenAI feature?" | Barred test, named incumbent |
| "is this defensible?" | Barred test |
| "who else is doing this?" | Competitor pass (Reach prep) |
| "should I build this?" | Full gap-scan on one idea |
| "/gap-scan" | Explicit invoke |

## What it isn't

- **Not** a market-research tool with no build decision attached. Scope is: real idea on the table, scan for whether it's a company.
- **Not** a competitive analysis of an already-shipped product. Different task.
- **Not** a pricing analysis. Different skill.
- **Not** a cheerleader. The default verdict for most ideas is FEATURE or HYPOTHESIS, not COMPANY. That's the point.

## Why it works

Both tests are falsifiable in a single evidence pass. "The incumbent won't build this because X" is a claim you can check: does X actually prevent them? "Here are my first 15 users" is a list you can read: are those humans or placeholder archetypes?

Most "is my idea good" tools skip these two tests because the answers are usually no. gap-scan was built to make the no visible, with the specific reason named, so the founder can decide whether to pivot or walk away before writing code.

The Barred test is a direct application of Thiel's "monopoly" framing from Zero to One (what makes you non-substitutable?), compressed into one named-incumbent check. The Reach test is a direct application of Paul Graham's "do things that don't scale" imperative (if you can't reach your first users by name, you don't have a market yet).

## Example

**Input:**

> I want to build a tool that generates summary emails for busy executives from their inbox.

**Output:**

```
VERDICT: FEATURE

Barred test: FAIL
- Best-positioned incumbent: Google (Gemini-in-Gmail), Microsoft (Copilot-in-Outlook)
- Both have the inbox, the AI, and the distribution. Zero structural conflict.
- Google already shipped "Help me summarize" in Gmail (2024). Microsoft shipped Copilot inbox summary in Outlook (2024).
- Timeline to absorption: already absorbed.

Reach test: PASS (but moot)
- You could reach the first 20 users via LinkedIn outreach to C-suite assistants.
- Does not matter because Barred fails.

Pivot direction:
If you still want to work in this space, name the segment where Gmail/Outlook refuse to ship. Candidates:
- SMB owners on self-hosted email (Fastmail, ProtonMail) where big incumbents won't integrate
- Regulated industries where inbox-content leaving the perimeter is a hard no
- Multi-inbox workflows (sales/support/exec combined) that neither Gmail nor Outlook addresses natively
```

That's the shape. The verdict is unambiguous, the Barred argument names the incumbent and the ship date, and the pivot direction is a specific research pointer.

## FAQ

**Which agents does this support?**
Claude Code (native skill), Cursor (`.cursor/rules/*.mdc` or `.cursorrules`), OpenAI Codex CLI (AGENTS.md), GitHub Copilot (copilot-instructions.md), Google Antigravity (rules file, format evolving), and any LLM that takes a system prompt.

**Does it work on Claude.ai (web)?**
Yes. Paste [`dist/generic-system-prompt/system-prompt.md`](dist/generic-system-prompt/system-prompt.md) into a Claude.ai project's custom instructions.

**What if my idea is in a space I know and the LLM doesn't?**
Supply the context in the prompt. The skill runs the Barred + Reach tests against whatever evidence you give it; richer evidence yields sharper verdicts. The skill will also do its own research pass, so bring facts, not vibes.

**Is this just Peter Thiel's "monopoly" test?**
The Barred test is a disciplined operationalization of it. Thiel's "secret" is poetic; "the best-positioned incumbent is structurally conflicted from building this" is specifically testable in one pass. The Reach test is from a different lineage (Y Combinator / Paul Graham) and catches the second common failure mode. Both together is the skill's addition.

**What if the verdict is COMPANY but I still think it's wrong?**
Then the Barred or Reach evidence is weak. Run gap-scan again with the specific objection as context. The skill is more useful as a conversation than a one-shot oracle.

## Contributing

New edge case the Barred or Reach test misses? Open an issue with a worked example.

New language translation? PR into [`docs/readme/`](./docs/readme/).

## License

MIT. See [LICENSE](LICENSE).

---

If gap-scan killed a bad idea before you wasted a month on it, star the repo. That's how I'll know it's working for people other than me.

---

## Origin

Built after watching too many founders (and myself) spend months on ideas that failed the Barred test on day one. The one-page template at [assets/GAP_SCAN_TEMPLATE.md](./assets/GAP_SCAN_TEMPLATE.md) was the artifact we needed before writing any code. This repo is that artifact + the protocol made invocable across every major AI coding agent.

Full protocol in [SKILL.md](SKILL.md). References for structural-conflict theory, research legs, pitch interrogation, and scoring rubric in [references/](./references/).
