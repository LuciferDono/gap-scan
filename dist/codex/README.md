# OpenAI Codex CLI install

Codex CLI reads `AGENTS.md` from the current working directory and `~/.codex/AGENTS.md` globally.

## Install (global)

```bash
mkdir -p ~/.codex && curl -fsSL https://raw.githubusercontent.com/LuciferDono/gap-scan/main/dist/codex/AGENTS.md -o ~/.codex/AGENTS.md
```

If you already have `~/.codex/AGENTS.md`, append rather than overwrite.

## Install (per-project)

```bash
curl -fsSL https://raw.githubusercontent.com/LuciferDono/gap-scan/main/dist/codex/AGENTS.md -o ./AGENTS.md
```

## Verify

Open Codex CLI in a directory with `AGENTS.md` present. Type "is this a company or feature" with some startup idea. Skill should transform.

## Trigger phrases

Same as Claude Code. Full list in the `AGENTS.md` file in this folder.
