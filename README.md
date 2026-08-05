# agent-skills

Agent Skills for [Claude Code](https://docs.claude.com/en/docs/claude-code), by [@conradmisz](https://github.com/conradmisz).

Each skill lives in its own folder under `skills/`, is self-contained, and has its own README with the full details.

## Skills

| Skill | What it does |
| ----- | ------------ |
| [project-kickoff](skills/project-kickoff) | Interviews you about a new project idea and writes the agent context files — `agentProjectDocs/` plus a root `CLAUDE.md` — so later sessions start with real context instead of re-deriving it |

## Installing

Replace `<skill>` with a name from the table above.

**Skills CLI**

```bash
npx skills add conradmisz/agent-skills@<skill>
```

**Claude Code plugin marketplace**

```
/plugin marketplace add conradmisz/agent-skills
/plugin install <skill>
```

**Manual**

```bash
git clone https://github.com/conradmisz/agent-skills.git
cp -r agent-skills/skills/<skill> ~/.claude/skills/
```

> [!NOTE]
> Skills run with your agent's full permissions. Read a skill's `SKILL.md` before installing it — mine included.

## License

[MIT](LICENSE)
