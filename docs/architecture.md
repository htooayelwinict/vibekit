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
- `packs/`: built-in setup packs with assistant-facing agents, commands, skills, and workflow guidance.
- `mcp/registry.psv`: MCP metadata used by `vibekit mcp`.
- `mcp/skills/`: MCP-specific skill overlays installed alongside MCP config.
- state directory: `${XDG_STATE_HOME:-~/.local/state}/vibekit`.

## Current Adapters

- Claude Code: Markdown agents, commands, skills, and `.mcp.json` for project MCP.
- OpenCode: Markdown agents, commands, skills, `AGENTS.md`, and `opencode.json` for MCP.
- Codex: a local Codex plugin marketplace under `${XDG_DATA_HOME:-~/.local/share}/vibekit/codex-marketplaces/vibekit/`, plugin commands, Markdown agents, portable skills, project `AGENTS.md`, and `~/.codex/config.toml` for MCP and plugin enablement.

## Self-Install Design

- `vibekit self install` copies `bin/`, `packs/`, and `mcp/` into `${XDG_DATA_HOME:-~/.local/share}/vibekit/self/<id>/` so the installed CLI does not depend on the original clone.
- The launcher at `<bin-dir>/vibekit` stores `source` and `runtime` markers, and the runtime metadata stores the launcher target path.
- Shell PATH updates are shell-specific: `zsh` uses `~/.zprofile`, `bash` uses `~/.bash_profile` or `~/.profile`, `fish` uses `${XDG_CONFIG_HOME:-~/.config}/fish/config.fish`, `nu` uses `${XDG_CONFIG_HOME:-~/.config}/nushell/config.nu`, and `pwsh` uses `~/.config/powershell/Microsoft.PowerShell_profile.ps1`.
- `vibekit self status` and `vibekit doctor` report the managed target, runtime, startup file, and a fresh-shell probe. When `--bin-dir` is omitted they prefer a Vibekit-managed launcher already on `PATH`.

## MCP Design

- MCP registry entries define transport, auth scheme, credential env var, setup URL, and docs URL.
- `vibekit mcp install` generates assistant-specific MCP config from registry metadata. Codex MCP config is written to `~/.codex/config.toml` because the Codex CLI does not read project `.codex/config.toml`.
- Local stdio MCPs can also carry credential env vars so Vibekit can prompt once and emit env references for assistants that support them.
- Local MCPs can also bootstrap managed runtimes under `${XDG_DATA_HOME:-~/.local/share}/vibekit/mcp-runtimes/` so generated configs can point at stable absolute launchers instead of depending on shell `PATH`. For Python tools this can include either a managed virtualenv or a managed `uv` installation plus `uv tool install`.
- Each MCP can also ship a matching `mcp-*` skill under `mcp/skills/`.
- MCP skill files are installed into each assistant's skill directory so they can be loaded explicitly at task time.
- The core planning, research, brainstorming, implementation, debugging, and review skills and agents point users toward these `mcp-*` skills when external context or second-pass reasoning is relevant.

## Codex Plugin Design

- Pack installs create a local marketplace with `.agents/plugins/marketplace.json` and `plugins/core-vibe-coder/.codex-plugin/plugin.json`.
- The Codex plugin contains `commands/`, `agents/`, `skills/`, and supplemental rules so slash commands and specialists are discoverable through Codex's plugin loader.
- Vibekit merges `[marketplaces.vibekit]` and `[plugins."core-vibe-coder@vibekit"]` into `~/.codex/config.toml`, then runs `codex plugin add core-vibe-coder@vibekit` to populate Codex's plugin cache.
- Project scope still writes `AGENTS.md` into the repository because that is the durable project-context surface Codex reads during normal coding sessions.

## Next Adapter Work

- Git URL pack installation.
- Pack manifest validation.
- Copilot/VS Code adapter.
