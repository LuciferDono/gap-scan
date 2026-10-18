# GitHub Copilot install

GitHub Copilot supports custom instructions at the repo level (`.github/copilot-instructions.md`) and the user level (VS Code settings).

## Install (per-repo)

```bash
mkdir -p .github
curl -fsSL https://raw.githubusercontent.com/LuciferDono/gap-scan/main/dist/copilot/copilot-instructions.md -o .github/copilot-instructions.md
```

## Install (VS Code user-level)

1. Open VS Code settings.json (Cmd/Ctrl+Shift+P → "Preferences: Open User Settings (JSON)").
2. Add `github.copilot.chat.codeGeneration.instructions` and paste the file body.

## JetBrains IDEs

Settings → GitHub Copilot → Instructions. Paste contents of `copilot-instructions.md`.

## Verify

Type "is this a company or feature" with startup idea in Copilot Chat. Skill should transform.

## Caveat

Copilot's adherence to long custom instructions is less reliable than Claude Code or Codex CLI. Explicit `/gap-scan` triggers work more consistently than natural-language phrases.
