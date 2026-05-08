<!-- vibekit:pack=core-vibe-coder -->
# Vibe Coding Setup

This project uses a vibekit-managed Claude Code setup.

Core expectations:

- Research existing patterns before editing.
- Keep changes small and reversible.
- Use specialized agents for planning, debugging, and review when helpful.
- Do not install or use MCP servers unless the user has explicitly enabled them.
- If the user has enabled an MCP, load the matching `mcp-*` skill before relying on it.
- Never write secrets into tracked project files.
