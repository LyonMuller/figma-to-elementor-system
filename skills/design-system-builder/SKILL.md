---
name: design-system-builder
description: Convert Figma colors, typography, spacing, radius, shadows, grids, and component patterns into a normalized Elementor-compatible design system before any page build.
---

# Design System Builder

## Responsibility

Normalize Figma design data against existing Elementor globals. This phase must complete before Elementor pages, templates, containers, or widgets are created.

## Token Model

Read existing Elementor Global Colors, Global Fonts, Theme Style, and reusable style conventions through Elementor MCP before producing the design system. Map Figma values into these groups when present:

- Primary colors
- Secondary colors
- Accent colors
- Neutral colors
- Semantic colors
- Text colors
- Background colors
- Border colors
- Global fonts
- Typography scale
- Font weights
- Font sizes
- Line heights
- Letter spacing
- Spacing tokens
- Radius tokens
- Shadow/effect tokens
- Grid tokens
- Component tokens

## Normalization Rules

- Prefer named Figma variables/styles over raw values.
- Map to existing Elementor global roles and project globals first, including Primary, Secondary, Text, Accent, and any site-specific globals returned by MCP.
- Do not create new Global Colors, Global Fonts, or invented tokens during normal conversion.
- Do not apply hardcoded hex, RGBA, sampled Figma colors, or raw font values to Elementor settings.
- Preserve unmatched raw Figma values only in notes, warnings, or recommendations.
- Recommend a new global only when the value is reusable, meaningful, and cannot be mapped to an existing Elementor global.
- Prefer existing Global Fonts and native typography controls over one-off type values.
- Prefer `rem` for typography scale, spacing, radius, and component spacing when Elementor controls support unit selection.
- Document any native Elementor control that only supports `px`; do not recommend CSS solely to convert units.
- Do not create a separate token for every one-off value. One-off Figma values should become divergences unless the user authorizes a new global or reusable token.

## Output

Update:

- `design_system.colors`
- `design_system.typography`
- `design_system.spacing`
- `design_system.radius`
- `design_system.shadows`
- `design_system.grids`
- `design_system.component_tokens`
- `elementor_mapping.global_colors`
- `elementor_mapping.global_fonts`
- `elementor_mapping.theme_style`
