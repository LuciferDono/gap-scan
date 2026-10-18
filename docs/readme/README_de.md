# gap-scan

[English](../../README.md) · [简体中文](./README_zh-CN.md) · [日本語](./README_ja.md) · [한국어](./README_ko.md) · [Español](./README_es.md) · [Deutsch](./README_de.md) · [Português (Brasil)](./README_pt-BR.md)

A portable prompt-skill that separates startup gaps that are real companies from gaps that are features waiting to be cloned. Applies the Barred test (incumbent structural conflict) and the Reach test (first 10-20 nameable users reachable today). Works across Claude Code, Cursor, Codex CLI, GitHub Copilot, Antigravity, and any system-prompt LLM.

Verdict is one of COMPANY, FEATURE, or HYPOTHESIS — with the Barred incumbent named, the first-users list produced, and the pivot direction if either test fails.

## Install

### Claude Code
```bash
git clone https://github.com/LuciferDono/gap-scan ~/.claude/skills/gap-scan
```

### Cursor
```bash
mkdir -p .cursor/rules && curl -fsSL https://raw.githubusercontent.com/LuciferDono/gap-scan/main/dist/cursor/gap-scan.mdc -o .cursor/rules/gap-scan.mdc
```

Other agents: see [`dist/`](../../dist/).

## Full docs

See the [English README](../../README.md) and [SKILL.md](../../SKILL.md).

A full de translation PR is welcome.

## License

MIT. [LICENSE](../../LICENSE).
