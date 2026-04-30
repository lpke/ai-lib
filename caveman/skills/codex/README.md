# Codex Skills

Codex can use repo-local skills from `.agents/skills/<skill-name>/SKILL.md`.

Install `caveman` in a project:

```sh
mkdir -p .agents/skills
ln -s "$PWD/caveman/skills/codex/caveman" .agents/skills/caveman
```

The `caveman` package also includes `hook.json` for users who want a Codex startup reminder.

