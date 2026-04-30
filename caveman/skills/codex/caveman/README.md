# Caveman Codex Skill

Codex skill package for compressed technical communication.

## Install

```sh
mkdir -p .agents/skills
ln -s "$PWD/caveman/skills/codex/caveman" .agents/skills/caveman
```

## Optional Startup Hook

To load a visible startup reminder, add the contents of `hook.json` to `.codex/hooks.json` under `SessionStart`, then enable hooks:

```toml
[features]
codex_hooks = true
```

