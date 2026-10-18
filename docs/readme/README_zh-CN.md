# gap-scan

[English](../../README.md) · **简体中文** · [日本語](./README_ja.md) · [한국어](./README_ko.md) · [Español](./README_es.md) · [Deutsch](./README_de.md) · [Português (Brasil)](./README_pt-BR.md)

一个可移植的 prompt 技能，用于区分「真正的公司机会」与「只是等待被巨头抄袭的 feature」。跨 Claude Code、Cursor、Codex CLI、GitHub Copilot、Antigravity 和任何支持 system prompt 的 LLM 工作。

## 问题

大多数 LLM「创业想法验证器」都告诉你你的想法很好。少数反对的会给你一份通用 PESTEL 分析。两者都没回答真正重要的两个问题。

**问题一（Barred 测试）：** 最佳位置的巨头是否在结构上无法构建这个？如果 OpenAI、Cursor、Google 或 Microsoft 可以把你的想法作为周末 feature 发布，你没有公司，你有一个等待被吸收的 feature。

**问题二（Reach 测试）：** 前 10-20 个用户是今天就可以触达的具名人类吗？如果你无法用姓名和联系渠道列出他们，你没有市场，你有一个假设。

任一测试失败，这个想法就不是一家公司，不管 TAM slide 声称市场有多大。

## 功能

gap-scan 在并行的证据环节上对两个测试进行验证，并最终给出三种判定之一：

- **COMPANY**：两项都通过。附上前 10 位用户名单、Barred 论证、保护你的结构性冲突。
- **FEATURE**：Barred 测试失败。点名可能吸收这一想法的巨头及时间线。
- **HYPOTHESIS**：Reach 测试失败。指出研究缺口：在这想法成为公司之前你需要采访谁。

## 安装

### Claude Code

```bash
git clone https://github.com/LuciferDono/gap-scan ~/.claude/skills/gap-scan
```

### Cursor

```bash
mkdir -p .cursor/rules && curl -fsSL https://raw.githubusercontent.com/LuciferDono/gap-scan/main/dist/cursor/gap-scan.mdc -o .cursor/rules/gap-scan.mdc
```

其他 agent 见 [`dist/`](../../dist/)。

## 触发词

"is this a company or a feature?", "untapped market", "should I build this?", "why isn't this just a Cursor feature?", "/gap-scan"。

## License

MIT。[LICENSE](../../LICENSE)。
