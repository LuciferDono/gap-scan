# Google Antigravity install

Antigravity (Google's autonomous coding IDE, late 2025) supports custom agent rules. Exact path still stabilizing.

## Best-known install paths

Try in order:

- `~/.antigravity/agents/` — global
- `.antigravity/rules/` — per-project
- `.gemini/` — legacy Gemini Code Assist path

Drop `gap-scan.md` into whichever location your Antigravity reads.

## Install (try first)

```bash
mkdir -p ~/.antigravity/agents
curl -fsSL https://raw.githubusercontent.com/LuciferDono/gap-scan/main/dist/antigravity/gap-scan.md -o ~/.antigravity/agents/gap-scan.md
```

## Verify

Type "is this a company or feature" after pasting startup idea. Skill should transform.

## Known unknowns

Rules format still evolving. If the path above doesn't work for your version, open an issue at https://github.com/LuciferDono/gap-scan/issues with your version's path.
