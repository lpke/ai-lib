To auto-activate caveman on startup or resume:

1. Add the contents of `hook.json` to `.codex/hooks.json` under `SessionStart`

```json
{
  "hooks": {
    "SessionStart": [
      <hook.json>
    ]
  }
}
```

2. Enable hooks in `.codex/config.toml`:

```toml
[features]
hooks = true
```

**Note:** The hook prints the SKILL.md directly into the prompt, as opposed to relying on the agent to read it. This is done because often the agent was being lazy and not reading it every time.
