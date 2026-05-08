---
name: mcp-figma
description: Use when implementing or reviewing UI from Figma files, frames, or design-system context.
---
<!-- vibekit:pack=mcp-figma -->

# Figma MCP

Use this skill when the task depends on Figma design context such as frame structure, spacing, type scale, components, variables, or design-system patterns.

Only use this skill if the Figma MCP tools are available in the current assistant. If they are not available, say that Figma is not configured and continue with repo-local UI context.

## Workflow

1. Start from the specific Figma link, frame, or file the user provided.
2. Extract the exact layout, components, spacing, typography, and variable usage that matter.
3. Map the design to existing app components and tokens before inventing new ones.
4. Call out ambiguous areas, missing assets, or mismatches with the current codebase.
5. Use the design context to guide implementation or review comments.

## Good Uses

- Implementing a screen from a Figma frame
- Comparing code to the source design
- Pulling design-system details into implementation planning

## Avoid

- Treating Figma as a substitute for reading the existing app code
- Guessing at a design when no specific file or frame was provided
