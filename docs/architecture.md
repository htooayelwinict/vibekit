# Architecture

Vibekit is a local-first Bash CLI that installs assistant workflow content into Claude Code, OpenCode, and Codex. The executable is intentionally self-contained: `bin/vibekit` owns command parsing, install planning, adapter mapping, state tracking, MCP config generation, and self-install behavior.

```text
repo content
  -> pack or MCP registry lookup
  -> adapter target expansion
  -> diff/install/uninstall action
  -> checksum-backed state record
```

## Source Of Truth

- `bin/vibekit`: CLI runtime and installer engine.
- `packs/core-vibe-coder/pack.env`: built-in pack metadata.
- `packs/core-vibe-coder/{claude,opencode,codex}/`: assistant-specific command and agent payloads.
- `packs/core-vibe-coder/skills/`: portable workflow skills installed for all supported assistants.
- `packs/core-vibe-coder/shared/AGENTS.md`: project context file used by OpenCode and Codex project installs.
- `mcp/registry.psv`: MCP server registry used by `vibekit mcp`.
- `mcp/skills/mcp-*/`: MCP-specific skill overlays installed alongside generated MCP config.
- `README.md`: user-facing quick start, command reference, and license notice.
- `docs/`: maintainer-facing architecture, codebase summary, and review notes.

## Core Flows

`vibekit diff` expands pack files for the selected tools and prints the action that install would take. It does not acquire the state lock and should remain read-only.

`vibekit install` expands the same file list, writes files, records checksums, and backs up overwritten files under `${XDG_STATE_HOME:-~/.local/state}/vibekit/backups/<timestamp>/`.

`vibekit uninstall` reads `${XDG_STATE_HOME:-~/.local/state}/vibekit/installed.tsv` and removes only files whose current checksum still matches the install record. Changed files are kept.

`vibekit status` compares tracked checksums with current files and reports `ok`, `changed`, or `missing`.

`vibekit self install` copies `bin/`, `packs/`, and `mcp/` into `${XDG_DATA_HOME:-~/.local/share}/vibekit/self/<id>/`, then writes a launcher at `<bin-dir>/vibekit` so the command can survive moving or deleting the original clone.

## State And Safety

- State lives under `${XDG_STATE_HOME:-~/.local/state}/vibekit`.
- Installs are serialized with a lock directory at `lock`.
- `installed.tsv` stores pack id, tool, scope, project key, target path, checksum, backup path, and install timestamp.
- `secrets.env` stores local secrets as shell exports with file mode `600` where supported.
- Existing user files are skipped unless they are already Vibekit-managed, contain a matching pack marker, or `--force` is passed.
- MCP config fragments are cached under `mcp-fragments/` so multiple MCP servers can share one assistant config file and uninstall can rebuild the remaining servers.

## Adapter Targets

Claude Code project installs write Markdown agents, commands, skills, and `CLAUDE.md` under `.claude/`. Project MCP config is `.mcp.json`. Global Claude MCP config is not written directly because Claude global MCP state is managed by Claude itself.

OpenCode project installs write Markdown agents, commands, skills, and shared `AGENTS.md` into the repository. Global installs use `${XDG_CONFIG_HOME:-~/.config}/opencode`. MCP config is `opencode.json`.

Codex installs create a local marketplace under `${XDG_DATA_HOME:-~/.local/share}/vibekit/codex-marketplaces/vibekit/` and place the pack as a Codex plugin. Vibekit merges `[marketplaces.vibekit]` and `[plugins."core-vibe-coder@vibekit"]` into `~/.codex/config.toml`, then tries `codex plugin add core-vibe-coder@vibekit` when the `codex` command is available. Project scope also writes `AGENTS.md` into the target project.

## MCP Design

Registry rows define the MCP id, display name, local or remote kind, endpoint or command, auth scheme, credential env var, setup URL, and docs URL.

Generated MCP config is adapter-specific:

- Claude uses JSON under `mcpServers`.
- OpenCode uses JSON under `mcp`.
- Codex uses TOML under `[mcp_servers.<id>]` in `~/.codex/config.toml`.

Remote MCPs can use header env vars, bearer token env vars, OAuth, or no auth. Local MCPs can emit command arrays and optional environment references. The `open-bridge` MCP is special: Vibekit can bootstrap a managed runtime under `${XDG_DATA_HOME:-~/.local/share}/vibekit/mcp-runtimes/open-bridge/` and generates a launcher that sources `secrets.env` before starting the server.

## Current Pack Shape

`core-vibe-coder` currently ships:

- 12 specialist agents per assistant.
- 10 slash-style commands per assistant: `brainstorm`, `code`, `deploy`, `docs`, `fix`, `plan`, `research`, `review`, `security`, and `test`.
- 13 portable skills covering planning, implementation, review, testing, debugging, documentation, research, security, DevOps, database changes, UI/UX, orchestration, and brainstorming.
- 6 MCP skill overlays: `context7`, `figma`, `github`, `open-bridge`, `playwright`, and `sentry`.

## Known Extension Points

- Git URL pack installation.
- Pack manifest validation beyond `pack.env`.
- Additional assistant adapters such as Copilot or VS Code.
- Stronger automated test coverage for install, uninstall, and MCP merge behavior.
