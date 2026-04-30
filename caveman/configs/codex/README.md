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
codex_hooks = true
```
