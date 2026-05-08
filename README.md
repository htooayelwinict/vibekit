# Vibekit

CLI-first setup manager for vibe coders.

Vibekit installs and tracks coding-assistant setup packs for Claude Code, OpenCode, and Codex. The MVP is local-first, Bash-based, and safe by default.

## Status

This is an early MVP scaffold.

Implemented:

- Tool detection
- Pack listing
- Dry-run diffs
- Safe install with backups and state tracking
- Safe uninstall by checksum
- Core Vibe Coder pack
- Claude Code adapter
- OpenCode adapter
- Codex adapter
- MCP installers for clean assistant config files plus matching `mcp-*` skills
- Local secret storage helper

## Quick Start

```bash
./bin/vibekit self install
vibekit doctor --shell zsh
vibekit diff core-vibe-coder --tools claude,opencode,codex --scope project
vibekit install core-vibe-coder --tools claude,opencode,codex --scope project
```

If you do not want to install a launcher yet, you can still run the repo-local script directly:

```bash
./bin/vibekit doctor --shell zsh
./bin/vibekit diff core-vibe-coder --tools claude,opencode,codex --scope project
./bin/vibekit install core-vibe-coder --tools claude,opencode,codex --scope project
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
vibekit secrets set CONTEXT7_API_KEY
```

## Safety Model

- Existing user files are skipped by default.
- `--force` is required to overwrite non-vibekit files.
- Backups are stored under `${XDG_STATE_HOME:-~/.local/state}/vibekit/backups`.
- Installed files are tracked in `${XDG_STATE_HOME:-~/.local/state}/vibekit/installed.tsv`.
- Uninstall removes only files whose checksum still matches the install record.
- Secrets are never written into project configs directly.

## Config Targets

Claude Code:

- Project: `.claude/agents`, `.claude/commands`, `.claude/skills`, `.claude/CLAUDE.md`
- Global: `~/.claude/agents`, `~/.claude/commands`, `~/.claude/skills`, `~/.claude/CLAUDE.md`

OpenCode:

- Project: `.opencode/agents`, `.opencode/commands`, `.opencode/skills`, `AGENTS.md`
- Global: `~/.config/opencode/agents`, `~/.config/opencode/commands`, `~/.config/opencode/skills`, `~/.config/opencode/AGENTS.md`

Codex:

- Project: `.codex/agents`, `.codex/rules`, `.agents/skills`
- Global: `~/.codex/agents`, `~/.codex/rules`, `~/.agents/skills`

## MCP

`vibekit mcp install` does two things:

- Writes the assistant-specific MCP config file for Claude, OpenCode, and/or Codex.
- Installs a matching `mcp-*` skill so planning, debugging, and review flows can explicitly load the right MCP guidance when relevant.

Current registry entries:

- `context7`: official docs lookup via API key header
- `playwright`: browser automation via local stdio server
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
./bin/vibekit mcp install figma --tools claude,opencode,codex --scope project
./bin/vibekit mcp uninstall context7 --tools claude,opencode,codex --scope project
```

Installed MCP skills are placed alongside each assistant's normal skills:

- Claude: `.claude/skills/mcp-<name>/SKILL.md`
- OpenCode: `.opencode/skills/mcp-<name>/SKILL.md`
- Codex: `.agents/skills/mcp-<name>/SKILL.md`

The built-in planning, debugging, and review setup is instructed to load these skills when a task needs external docs, GitHub state, browser checks, design context, or production incident data.

Claude global MCP configuration is intentionally not written directly in MVP because Claude stores user/global MCP state in `~/.claude.json`. Use Claude's own command for global Claude MCP setup:

```bash
claude mcp add --transport http context7 https://mcp.context7.com/mcp
```

For Claude global Playwright MCP setup, use Claude's command:

```bash
claude mcp add --transport stdio playwright -- npx -y @playwright/mcp@latest
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
