# Claude Code install

Claude Code auto-discovers skills under `~/.claude/skills/`. The canonical `SKILL.md` at the repo root is the file Claude Code reads.

## Install

```bash
git clone https://github.com/LuciferDono/gap-scan ~/.claude/skills/gap-scan
```

Windows (PowerShell):

```powershell
git clone https://github.com/LuciferDono/gap-scan "$env:USERPROFILE\.claude\skills\gap-scan"
```

## Verify

In any Claude Code session, type `/gap-scan` or paste some AI-generated text and say "is this a company or feature." The skill should fire and produce the Transform output described in `../../SKILL.md`.

## Update

```bash
cd ~/.claude/skills/gap-scan && git pull
```

## Trigger phrases

"is this a company or feature", "unai", "sound human", "remove AI", "/gap-scan". Full list in `../../SKILL.md`.
