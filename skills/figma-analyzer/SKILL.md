---
name: figma-analyzer
description: Analyze Figma files, frames, nodes, components, variants, variables, styles, screenshots, auto layouts, grids, hierarchy, and assets for Figma to Elementor conversion workflows.
---

# Figma Analyzer

## Responsibility

Read the Figma source through MCP and populate `figma_analysis` in the internal contract. This phase is read-only against Figma unless the user explicitly asks for Figma canvas edits.

## Required Workflow

1. Parse the Figma URL or selected node.
2. Call `get_design_context` first for the target frame or node.
3. Call `get_variable_defs` to extract variables and styles used by the selection.
4. Call `get_screenshot` for the same target to preserve a visual reference.
5. If the design is too large, call `get_metadata`, identify major child nodes, then fetch each major node with `get_design_context`.
6. Capture components, instances, variants, layout direction, sizing, constraints, text styles, color styles, effects, grids, images, icons, and hierarchy.
7. Record uncertainty explicitly in `implementation.warnings`.

## Figma Data Rules

- Treat React/Tailwind-like output from Figma MCP as design context, not final implementation code.
- Prefer Figma variables and styles over raw visual values when both are available.
- Keep screenshots as validation references.
- Do not hallucinate missing nodes, variant axes, or asset sources.
- If asset URLs are returned by the MCP server, preserve the source URL and intended use.

## Output

Update:

- `project.figma_url`
- `project.figma_node`
- `figma_analysis.frames`
- `figma_analysis.nodes`
- `figma_analysis.components`
- `figma_analysis.variants`
- `figma_analysis.color_styles`
- `figma_analysis.text_styles`
- `figma_analysis.layout_patterns`
- `figma_analysis.assets`
- `figma_analysis.effects`
