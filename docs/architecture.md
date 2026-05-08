# Architecture

Vibekit uses a simple adapter model.

```text
pack content
  -> install planner
  -> tool adapter
  -> assistant-specific files
  -> state tracking
```

## Core Modules

- `bin/vibekit`: Bash CLI and installer engine.
- `packs/`: built-in setup packs.
- `mcp/registry.psv`: MCP metadata used by `vibekit mcp`.
- `mcp/skills/`: MCP-specific skill overlays installed alongside MCP config.
- state directory: `${XDG_STATE_HOME:-~/.local/state}/vibekit`.

## Current Adapters

- Claude Code: Markdown agents, commands, skills, and `.mcp.json` for project MCP.
- OpenCode: Markdown agents, commands, skills, `AGENTS.md`, and `opencode.json` for MCP.
- Codex: TOML agents, Starlark rules, portable skills, and `config.toml` for MCP.

## Self-Install Design

- `vibekit self install` copies `bin/`, `packs/`, and `mcp/` into `${XDG_DATA_HOME:-~/.local/share}/vibekit/self/<id>/` so the installed CLI does not depend on the original clone.
- The launcher at `<bin-dir>/vibekit` stores `source` and `runtime` markers, and the runtime metadata stores the launcher target path.
- Shell PATH updates are shell-specific: `zsh` uses `~/.zprofile`, `bash` uses `~/.bash_profile` or `~/.profile`, `fish` uses `${XDG_CONFIG_HOME:-~/.config}/fish/config.fish`, `nu` uses `${XDG_CONFIG_HOME:-~/.config}/nushell/config.nu`, and `pwsh` uses `~/.config/powershell/Microsoft.PowerShell_profile.ps1`.
- `vibekit self status` and `vibekit doctor` report the managed target, runtime, startup file, and a fresh-shell probe. When `--bin-dir` is omitted they prefer a Vibekit-managed launcher already on `PATH`.

## MCP Design

- MCP registry entries define transport, auth scheme, credential env var, setup URL, and docs URL.
- `vibekit mcp install` generates assistant-specific MCP config from registry metadata.
- Each MCP can also ship a matching `mcp-*` skill under `mcp/skills/`.
- MCP skill files are installed into each assistant's skill directory so they can be loaded explicitly at task time.
- The core planning, debugging, and review skills and agents point users toward these `mcp-*` skills when external context is relevant.

## Next Adapter Work

- JSON/TOML merge instead of clean-file-only MCP installs.
- Git URL pack installation.
- Pack manifest validation.
- Copilot/VS Code adapter.
