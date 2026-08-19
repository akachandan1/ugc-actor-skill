# Installing this skill

This repo contains a single `SKILL.md` using the standard Agent Skills format (YAML frontmatter with `name` + `description`, followed by instructions). That format is portable across Claude Code, Codex CLI, and other compatible agents — install it by copying `SKILL.md` into the right folder for your tool.

## Claude Code

Claude Code looks for skills in two places, project skills taking priority over personal ones:

| Scope | Location |
|---|---|
| Personal (all projects) | `~/.claude/skills/ugc-actor/SKILL.md` |
| Project-only | `.claude/skills/ugc-actor/SKILL.md` (inside your repo) |

**Install (personal, all projects):**

```bash
mkdir -p ~/.claude/skills/ugc-actor
curl -sL https://raw.githubusercontent.com/akachandan1/ugc-actor-skill/main/SKILL.md -o ~/.claude/skills/ugc-actor/SKILL.md
```

Or clone the whole repo directly into place:

```bash
git clone https://github.com/akachandan1/ugc-actor-skill.git ~/.claude/skills/ugc-actor
```

Restart Claude Code (or start a new session). The skill is auto-discovered from its `description` — just ask for a UGC actor, or invoke it explicitly if your setup uses named skills.

## Codex CLI (OpenAI)

Codex CLI scans for skills in this order: repo-level, then user-level, then admin-level, then built-ins.

| Scope | Location |
|---|---|
| Personal (all projects) | `$HOME/.agents/skills/ugc-actor/SKILL.md` |
| Project-only | `.agents/skills/ugc-actor/SKILL.md` (inside your repo, searched up to repo root) |

**Install (personal, all projects):**

```bash
mkdir -p ~/.agents/skills/ugc-actor
curl -sL https://raw.githubusercontent.com/akachandan1/ugc-actor-skill/main/SKILL.md -o ~/.agents/skills/ugc-actor/SKILL.md
```

Or clone the whole repo directly into place:

```bash
git clone https://github.com/akachandan1/ugc-actor-skill.git ~/.agents/skills/ugc-actor
```

Restart Codex CLI. If the skill doesn't show up, double check `SKILL.md` has valid `name` + `description` frontmatter (it does in this repo) and that Codex has been restarted after adding it.

To disable it later without deleting it, add to `~/.codex/config.toml`:

```toml
[[skills.config]]
path = "~/.agents/skills/ugc-actor/SKILL.md"
enabled = false
```

## Notes

- This skill has no external dependencies — it's pure instructions, no scripts or assets required.
- Works the same way in both tools since both consume the same `SKILL.md` format.
