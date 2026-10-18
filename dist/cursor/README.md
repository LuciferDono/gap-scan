# Cursor install

Cursor supports two rules formats:

- **Modern (Cursor 0.45+):** `.cursor/rules/*.mdc` files with frontmatter. `alwaysApply: true` activates on every request.
- **Legacy:** a single `.cursorrules` file at the project root.

## Install — modern (recommended)

```bash
mkdir -p .cursor/rules
curl -fsSL https://raw.githubusercontent.com/LuciferDono/gap-scan/main/dist/cursor/gap-scan.mdc -o .cursor/rules/gap-scan.mdc
```

## Install — legacy

```bash
curl -fsSL https://raw.githubusercontent.com/LuciferDono/gap-scan/main/dist/cursor/.cursorrules -o .cursorrules
```

## User-level / global rules

Cursor Settings → Rules for AI. Paste the contents of `gap-scan.mdc` (skip the frontmatter).

## Verify

After pasting startup idea to Cursor's agent, type "is this a company or feature." The skill should transform it.

## Caveat

Cursor's single-agent execution means the adversarial loop (max 3 passes) runs sequentially within one generation, not as separate agent calls. Reasoning gain is similar to Claude Code's inline mode.
