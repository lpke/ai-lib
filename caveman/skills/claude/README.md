# Claude Skills

Claude Code discovers skills from these locations:

- Personal: `~/.claude/skills/<skill-name>/SKILL.md`
- Project: `.claude/skills/<skill-name>/SKILL.md`

Install `caveman` as a personal skill:

```sh
mkdir -p ~/.claude/skills
ln -s "$PWD/caveman/skills/claude/caveman" ~/.claude/skills/caveman
```

Install `caveman` in a project:

```sh
mkdir -p .claude/skills
ln -s "$PWD/caveman/skills/claude/caveman" .claude/skills/caveman
```

