To auto-activate caveman on startup or resume:

1. Add the contents of `hook_lite.json` or `hook_full.json` to `.codex/hooks.json` under `SessionStart`

```json
{
  "hooks": {
    "SessionStart": [
      <hook_[lite|full].json>
    ]
  }
}
```

2. Enable hooks in `.codex/config.toml`:

```toml
[features]
codex_hooks = true
```
