---
name: ui-ux-design
description: Design and implement accessible, consistent UI changes using the repo's existing component and styling patterns.
---
<!-- vibekit:pack=core-vibe-coder -->

# UI UX Design

Use this skill when the work is primarily interface design, component behavior, accessibility, or responsive polish.

## Workflow

1. Audit the repo for existing UI primitives and page patterns.
2. If the user enabled Figma MCP, load `mcp-figma` for design context.
3. Prefer the existing design system before inventing new primitives.
4. Cover loading, empty, success, and error states.
5. If the user enabled Playwright MCP, use it for browser verification across key viewports.
6. If interaction trade-offs or UX copy direction are unclear and the user enabled Open Bridge, use `mcp-open-bridge` for an extra comparison pass.

## Relevant MCP Skills

- `mcp-figma` for design files and component intent
- `mcp-playwright` for browser and responsive verification
- `mcp-context7` for framework-specific accessibility or component patterns
- `mcp-open-bridge` for alternative interaction ideas, copy options, and synthesis across design constraints

## Output

Include:

- UI goal
- Existing pattern used
- States covered
- Accessibility checks
- Verification run
