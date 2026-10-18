# gap-scan — per-agent packagings

The canonical skill lives in `../SKILL.md`. This directory holds platform-specific wrappers.

| Agent | Install file | Path on disk |
|-------|-------------|-------------|
| [Claude Code](./claude-code/) | `../SKILL.md` | `~/.claude/skills/gap-scan/` |
| [Cursor](./cursor/) | `cursor/gap-scan.mdc` or `.cursorrules` | `.cursor/rules/` or project root |
| [OpenAI Codex CLI](./codex/) | `codex/AGENTS.md` | `~/.codex/AGENTS.md` or `./AGENTS.md` |
| [GitHub Copilot](./copilot/) | `copilot/copilot-instructions.md` | `.github/copilot-instructions.md` |
| [Google Antigravity](./antigravity/) | `antigravity/gap-scan.md` | `~/.antigravity/agents/` |
| [Any system-prompt LLM](./generic-system-prompt/) | `generic-system-prompt/system-prompt.md` | paste into system prompt field |

Each folder has a per-agent README with install commands.
