# Caveman

`caveman` is a terse communication mode for agents. It cuts filler while keeping technical accuracy, code, errors, warnings, and irreversible-action confirmations clear.

See: [JuliusBrussee/caveman](https://github.com/JuliusBrussee/caveman)

## Variants

- `lite`: tight professional prose, keeps articles and full sentences.
- `full`: default caveman style, drops articles and allows fragments.
- `ultra`: most compressed style, uses abbreviations and arrows when clear.

## Layout

```
caveman/
├── prompts/               # Standalone prompt bodies
└── skills/
    ├── claude/caveman/    # Install to .claude/skills/caveman (project or home level)
    └── codex/caveman/     # Install to .agents/skills/caveman (project or home level)
```

## Install Targets

Claude personal skill:

```sh
ln -s "$PWD/caveman/skills/claude/caveman" ~/.claude/skills/caveman
```

Claude project skill:

```sh
mkdir -p .claude/skills
ln -s "$PWD/caveman/skills/claude/caveman" .claude/skills/caveman
```

Codex skill:

```sh
mkdir -p .agents/skills
ln -s "$PWD/caveman/skills/codex/caveman" .agents/skills/caveman
```

See each package README for agent-specific notes.
