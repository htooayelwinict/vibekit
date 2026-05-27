<p align="center">
  <img src="assets/vibekit-banner.svg" alt="Animated Vibekit banner" width="100%" />
</p>

<h1 align="center">Vibekit</h1>

<p align="center"><strong>Local-first setup manager for coding assistants, workflow packs, MCP servers, and clean teardown.</strong></p>

<p align="center">
  Install once. Diff before writing. Track every file. Cleanly uninstall when the experiment is done.
</p>

<p align="center">
  <img alt="Status early MVP" src="https://img.shields.io/badge/status-early_mvp-7c3aed?style=for-the-badge" />
  <img alt="Runtime Bash" src="https://img.shields.io/badge/runtime-bash-111827?style=for-the-badge&logo=gnubash&logoColor=white" />
  <img alt="Platform macOS and Linux" src="https://img.shields.io/badge/platform-macOS%20%7C%20Linux-0f172a?style=for-the-badge" />
  <img alt="Assistants Claude OpenCode Codex" src="https://img.shields.io/badge/assistants-Claude%20Code%20%7C%20OpenCode%20%7C%20Codex-0f766e?style=for-the-badge" />
  <a href="https://fossmyanmar.org/"><img alt="FOSS Myanmar free and open source software" src="https://img.shields.io/badge/FOSS-Myanmar-16a34a?style=for-the-badge" /></a>
  <img alt="License personal use only" src="https://img.shields.io/badge/license-personal_use_only-dc2626?style=for-the-badge" />
</p>

<p align="center">
  <a href="#quick-start"><strong>Quick Start</strong></a>
  |
  <a href="#install-the-cli"><strong>Install</strong></a>
  |
  <a href="#clean-uninstall-and-secret-cleanup"><strong>Uninstall</strong></a>
  |
  <a href="#mcp"><strong>MCP</strong></a>
  |
  <a href="#foss-myanmar"><strong>FOSS Myanmar</strong></a>
  |
  <a href="docs/architecture.md"><strong>Architecture</strong></a>
</p>

> [!IMPORTANT]
> Vibekit is source-available for personal use only.
> Commercial use is not allowed.
> Use on company-owned or company-managed devices is not allowed.
> See `LICENSE` for the full terms.

```text
+-----------------------------------------------------------------------------+
|  Vibekit                                                                    |
+-----------------------------------------------------------------------------+
|  packs        -> commands, agents, skills, and project operating rules       |
|  mcp          -> assistant config plus matching mcp-* skills                 |
|  secrets      -> local state helper, never written into project configs      |
|  uninstall    -> checksum guarded cleanup with optional secret purge         |
+-----------------------------------------------------------------------------+
```

Vibekit installs and tracks coding-assistant setup packs for Claude Code, OpenCode, and Codex. The MVP is Bash-based, local-first, and built around one rule: show what will change before writing anything, then remember exactly what was written.

## Why It Exists

| Need | Vibekit answer |
| --- | --- |
| Try a serious assistant workflow without hand-copying files | Install the `core-vibe-coder` pack for Claude Code, OpenCode, and Codex. |
| Keep generated configs understandable | Use `vibekit diff` before install and checksum-backed state after install. |
| Add MCP servers without remembering every assistant's config shape | Generate Claude, OpenCode, and Codex MCP config from one registry. |
| Keep secrets out of project files | Store local credentials in `${XDG_STATE_HOME:-~/.local/state}/vibekit/secrets.env`. |
| Undo cleanly | Use pack uninstall, MCP uninstall, self uninstall, and `--purge-secrets` when credentials should be removed too. |

## Status

This is an early MVP scaffold.

Implemented:

- Tool detection
- Pack listing
- Dry-run diffs
- Safe install with backups and state tracking
- Safe uninstall by checksum
- Core Vibe Coder pack with persistent planning, implementation, research, review, and specialist workflows
- Claude Code adapter
- OpenCode adapter
- Codex adapter
- MCP installers for clean assistant config files plus matching `mcp-*` skills
- Local secret storage helper
- MCP uninstall with optional secret purge

## Quick Start

Install the CLI launcher, check your environment, preview the pack, then install:

```bash
./bin/vibekit self install
vibekit doctor --shell zsh
vibekit diff core-vibe-coder --tools claude,opencode,codex --scope project
vibekit install core-vibe-coder --tools claude,opencode,codex --scope project
```

Prefer not to install a launcher yet? Run the repo-local script directly:

```bash
./bin/vibekit doctor --shell zsh
./bin/vibekit diff core-vibe-coder --tools claude,opencode,codex --scope project
./bin/vibekit install core-vibe-coder --tools claude,opencode,codex --scope project
```

Add an MCP server and keep the matching assistant skill close by:

```bash
vibekit mcp diff github --tools claude,opencode,codex --scope project
vibekit mcp install github --tools claude,opencode,codex --scope project
```

## Install The CLI

Install a user-scoped launcher plus a self-contained runtime so `vibekit` works from any directory even if you later move or delete the clone you installed from:

```bash
./bin/vibekit self install
```

Default install target:

- `~/.local/bin/vibekit`
- runtime copy under `${XDG_DATA_HOME:-~/.local/share}/vibekit/self/`

Useful commands:

```bash
./bin/vibekit self status --shell auto
./bin/vibekit self install --force
./bin/vibekit self install --shell bash --bin-dir "$HOME/bin"
./bin/vibekit self uninstall --shell zsh
./bin/vibekit doctor --shell zsh
```

If the install bin dir is not already on your `PATH`, `vibekit self install` appends it to the default shell startup file for your shell:

- `zsh`: `~/.zprofile`
- `bash`: `~/.bash_profile` or `~/.profile`
- `fish`: `${XDG_CONFIG_HOME:-~/.config}/fish/config.fish`
- `nu`: `${XDG_CONFIG_HOME:-~/.config}/nushell/config.nu`
- `pwsh`: `~/.config/powershell/Microsoft.PowerShell_profile.ps1`

`vibekit self status` and `vibekit doctor` report:

- `shell-type`: normalized shell id used for startup-file and probe logic
- `shell-config`: startup file Vibekit would edit for that shell
- `shell-path`: whether that file already references the selected `--bin-dir`
- `fresh-shell`: whether a newly launched shell sees `vibekit` on `PATH`

When `--bin-dir` is omitted, `vibekit self status` and `vibekit doctor` prefer a Vibekit-managed launcher already on `PATH`; otherwise they fall back to `~/.local/bin`.

Then open a new terminal, or reload your shell with:

```bash
exec zsh -l
```

Re-run `./bin/vibekit self install` from a newer clone to refresh the installed runtime.

## Install Recipes

Preview before writing:

```bash
vibekit diff core-vibe-coder --tools claude,opencode,codex --scope project
vibekit mcp diff context7 --tools claude,opencode,codex --scope project
```

Install the default workflow pack:

```bash
vibekit install core-vibe-coder --tools claude,opencode,codex --scope project
```

Install MCP support with stored local secrets when prompted:

```bash
vibekit mcp install context7 --tools claude,opencode,codex --scope project
vibekit mcp install open-bridge --tools claude,opencode,codex --scope project
```

Store or rotate a secret directly:

```bash
vibekit secrets set CONTEXT7_API_KEY
vibekit secrets set OPENROUTER_API_KEY
vibekit secrets set OPENROUTER_MODEL
```

## Clean Uninstall And Secret Cleanup

Vibekit has three cleanup layers: installed pack files, installed MCP config/skills, and the self-installed CLI runtime.

Remove the Core Vibe Coder pack from the current project:

```bash
vibekit uninstall core-vibe-coder --tools claude,opencode,codex --scope project
```

Remove an MCP server but keep any stored credential for a future reinstall:

```bash
vibekit mcp uninstall github --tools claude,opencode,codex --scope project
```

Remove an MCP server and purge its stored secrets non-interactively:

```bash
vibekit mcp uninstall github --tools claude,opencode,codex --scope project --purge-secrets
```

Remove one stored secret directly:

```bash
vibekit secrets unset GITHUB_PAT_TOKEN
vibekit secrets unset CONTEXT7_API_KEY
vibekit secrets unset OPENROUTER_API_KEY
vibekit secrets unset OPENROUTER_MODEL
```

Secret cleanup guide:

| Goal | Command |
| --- | --- |
| Remove MCP config and keep credentials | `vibekit mcp uninstall <server> --tools claude,opencode,codex --scope project` |
| Remove MCP config and related credentials | `vibekit mcp uninstall <server> --tools claude,opencode,codex --scope project --purge-secrets` |
| Remove one named secret | `vibekit secrets unset <NAME>` |
| Remove the Vibekit launcher/runtime | `vibekit self uninstall --shell zsh` |

Remove the user-scoped launcher and copied runtime:

```bash
vibekit self uninstall --shell zsh
```

Uninstall safety rules:

- Pack uninstall removes only files whose checksum still matches Vibekit's install record.
- MCP uninstall rewrites shared config files when other Vibekit-managed MCP servers remain.
- `--purge-secrets` removes stored MCP-related secrets from `${XDG_STATE_HOME:-~/.local/state}/vibekit/secrets.env`.
- Self uninstall removes only a Vibekit-managed launcher and runtime.
- Shell startup files are not aggressively rewritten during self uninstall; remove the `# vibekit:path` block manually if you no longer want the bin dir on `PATH`.

## Commands

```bash
vibekit detect
vibekit doctor [--shell auto|zsh|bash|fish|nu|pwsh] [--bin-dir DIR]
vibekit self status [--shell auto|zsh|bash|fish|nu|pwsh] [--bin-dir DIR]
vibekit self install [--shell auto|zsh|bash|fish|nu|pwsh] [--bin-dir DIR] [--force]
vibekit self uninstall [--shell auto|zsh|bash|fish|nu|pwsh] [--bin-dir DIR]
vibekit status
vibekit list packs
vibekit mcp list
vibekit diff [pack]
vibekit install [pack]
vibekit uninstall [pack]
vibekit mcp diff context7
vibekit mcp install context7
vibekit mcp uninstall context7
vibekit mcp install playwright
vibekit mcp uninstall open-bridge --purge-secrets
vibekit secrets set CONTEXT7_API_KEY
vibekit secrets unset CONTEXT7_API_KEY
```

## Safety Model

- Existing user files are skipped by default.
- `--force` is required to overwrite non-vibekit files.
- Backups are stored under `${XDG_STATE_HOME:-~/.local/state}/vibekit/backups`.
- Installed files are tracked in `${XDG_STATE_HOME:-~/.local/state}/vibekit/installed.tsv`.
- Uninstall removes only files whose checksum still matches the install record.
- Secrets are never written into project configs directly.
- `--purge-secrets` can remove MCP-related local secrets during MCP uninstall.

## Config Targets

Claude Code:

- Project: `.claude/agents`, `.claude/commands`, `.claude/skills`, `.claude/CLAUDE.md`
- Global: `~/.claude/agents`, `~/.claude/commands`, `~/.claude/skills`, `~/.claude/CLAUDE.md`

OpenCode:

- Project: `.opencode/agents`, `.opencode/commands`, `.opencode/skills`, `AGENTS.md`
- Global: `~/.config/opencode/agents`, `~/.config/opencode/commands`, `~/.config/opencode/skills`, `~/.config/opencode/AGENTS.md`

Codex:

- Project: project `AGENTS.md` plus a local Codex plugin marketplace under `${XDG_DATA_HOME:-~/.local/share}/vibekit/codex-marketplaces/vibekit/`
- Global: the same local Codex plugin marketplace without a project `AGENTS.md`

Vibekit installs Codex packs as a real Codex plugin, then runs `codex plugin add core-vibe-coder@vibekit` so Codex caches and enables the plugin. The plugin contains Codex commands, specialist agents, and skills. Codex currently reads MCP config from `~/.codex/config.toml`, not project `.codex/config.toml`, so Vibekit installs Codex MCP entries into `~/.codex/config.toml` even when `--scope project` is selected.

## MCP

`vibekit mcp install` does two things:

- Writes the assistant-specific MCP config file for Claude, OpenCode, and/or Codex.
- Installs a matching `mcp-*` skill so planning, debugging, and review flows can explicitly load the right MCP guidance when relevant.

Current registry entries:

- `context7`: official docs lookup via API key header
- `playwright`: browser automation via local stdio server
- `open-bridge`: local OpenRouter-backed reasoning, synthesis, and second-opinion analysis
- `sentry`: remote OAuth MCP for production issue investigation
- `figma`: remote OAuth MCP for design context
- `github`: remote bearer-token MCP for issues, PRs, workflows, and releases

```bash
./bin/vibekit mcp list
./bin/vibekit mcp diff context7 --tools claude,opencode,codex --scope project
./bin/vibekit mcp install context7 --tools claude,opencode,codex --scope project
./bin/vibekit mcp install sentry --tools claude,opencode,codex --scope project
./bin/vibekit mcp install github --tools claude,opencode,codex --scope project
./bin/vibekit mcp install playwright --tools claude,opencode,codex --scope project
./bin/vibekit mcp install open-bridge --tools claude,opencode,codex --scope project
./bin/vibekit mcp install figma --tools claude,opencode,codex --scope project
./bin/vibekit mcp uninstall context7 --tools claude,opencode,codex --scope project
./bin/vibekit mcp uninstall open-bridge --tools codex --scope project --purge-secrets
```

Installed MCP skills are placed alongside each assistant's normal skills:

- Claude: `.claude/skills/mcp-<name>/SKILL.md`
- OpenCode: `.opencode/skills/mcp-<name>/SKILL.md`
- Codex: `~/.codex/skills/mcp-<name>/SKILL.md`

The built-in planning, research, brainstorming, implementation, debugging, and review setup is instructed to load these skills when a task needs external docs, GitHub state, browser checks, design context, production incident data, or a second-opinion reasoning pass.

`open-bridge` requires `OPENROUTER_API_KEY` plus a local bridge runtime. During install, Vibekit also offers an `OPENROUTER_MODEL` selection and stores it in the same secrets file. The upstream project supports `pip install openrouter-mcp-bridge` and `uvx openrouter-mcp-bridge`. Vibekit now bootstraps a managed runtime under `${XDG_DATA_HOME:-~/.local/share}/vibekit/mcp-runtimes/open-bridge/`, then points the generated MCP config at a Vibekit-managed launcher that loads Vibekit's secrets file before starting the server.

Runtime bootstrap rules:

- Prefer `python3.12`, `python3.11`, or `python3.10` and install `openrouter-mcp-bridge` into a managed virtualenv.
- If a compatible Python is not available, use `uv` to install the tool with `uv tool install --python 3.10 openrouter-mcp-bridge`.
- If `uv` is missing, install a managed copy of `uv` with Astral's official installer into Vibekit's runtime directory.
- On macOS package managers, install `uv` rather than a separate `uvx` formula. `uvx` is an alias provided by `uv`.

Because the managed launcher loads `${XDG_STATE_HOME:-~/.local/state}/vibekit/secrets.env`, Claude, OpenCode, and Codex can all receive `OPENROUTER_API_KEY` and `OPENROUTER_MODEL` without relying on the shell that launched the assistant.

On MCP uninstall, Vibekit asks whether to keep stored MCP secrets for future reinstall or remove them completely. Use `--purge-secrets` for non-interactive cleanup, or `vibekit secrets unset <NAME>` to remove a single stored value.

Claude global MCP configuration is intentionally not written directly in MVP because Claude stores user/global MCP state in `~/.claude.json`. Use Claude's own command for global Claude MCP setup:

```bash
claude mcp add --transport http context7 https://mcp.context7.com/mcp
```

For Claude global Playwright MCP setup, use Claude's command:

```bash
claude mcp add --transport stdio playwright -- npx -y @playwright/mcp@latest
```

For Claude global Open Bridge MCP setup, export `OPENROUTER_API_KEY` first and then use Claude's command:

```bash
claude mcp add --transport stdio open-bridge --env OPENROUTER_API_KEY="$OPENROUTER_API_KEY" -- uvx openrouter-mcp-bridge
```

For Claude global GitHub MCP setup, use Claude's command with a PAT header:

```bash
claude mcp add --transport http github https://api.githubcopilot.com/mcp/ \
  --header "Authorization: Bearer YOUR_GITHUB_PAT"
```

For Claude global Sentry or Figma MCP setup, use Claude's command and then authenticate in `/mcp`:

```bash
claude mcp add --transport http sentry https://mcp.sentry.dev/mcp
claude mcp add --transport http figma https://mcp.figma.com/mcp
```

## Reference Corpus

The sibling `claude-config` directory is a reference corpus only. It should not be copied wholesale into arbitrary projects because it is Claude-specific, stack-biased, and includes permissive local settings.

## FOSS Myanmar

Vibekit supports the spirit of Free and Open Source Software and links to the FOSS Myanmar community:

- https://fossmyanmar.org/

FOSS Myanmar is a community/site reference for free and open-source software. The legal terms for this repository are still defined by the `LICENSE` file below. To make Vibekit fully open source, replace `LICENSE` with a recognized FOSS license such as MIT, Apache-2.0, GPL-3.0, or AGPL-3.0.

## License

Copyright (c) 2026 `htooayelwinict`.

Vibekit is released under the `Vibekit Personal Use Only License 1.0`.

You may:

- use, copy, and modify Vibekit for your own personal, non-commercial use
- run it on devices you personally own or personally control for private use
- share original or modified copies only if the same personal-use-only terms and copyright notice stay with the code

You may not:

- use Vibekit for commercial work, internal business work, client work, or paid services
- use Vibekit on company-owned, employer-managed, or other organization-managed devices
- sell, sublicense, host, or redistribute Vibekit under different terms

See `LICENSE` for the full text.
