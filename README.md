# AI Prompt Library

Shared prompt and skill assets for agentic workflows.

## Structure

`<directory>/`

- `prompts/`: general, portable, provider-agnostic prompt file/s
- `skills/<skill>/SKILL.md`: skill files for providers to consume
- `configs/`: provider-specific config files and/or instructions

## Installing Skills

Every provider has different conventions.

### Codex (OpenAI):

Docs: [developers.openai.com/codex/skills](https://developers.openai.com/codex/skills)

Location: `.agents/skills/<skill>/SKILL.md`

`.agents/` can be provided in the home dir or project level.

### Claude (Anthropic)

Docs: [code.claude.com/docs/en/skills](https://code.claude.com/docs/en/skills)

Location: `.claude/skills/<skill>/SKILL.md`

`.claude/` can be provided in the home dir or project level.

---

## Symlinking

Use symlinks when you want one shared skill source instead of copying files into each provider directory.

```sh
# Codex
mkdir -p "<location>/.agents/skills"
ln -s "$HOME/.local/share/ai-lib/<path-to-skill>" "<location>/.agents/skills/<skill>"

# Claude
mkdir -p "<location>/.claude/skills"
ln -s "$HOME/.local/share/ai-lib/<path-to-skill>" "<location>/.claude/skills/<skill>"
```
