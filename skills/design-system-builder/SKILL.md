---
name: design-system-builder
description: Convert Figma colors, typography, spacing, radius, shadows, grids, and component patterns into a normalized Elementor-compatible design system before any page build.
---

# Design System Builder

## Responsibility

Normalize Figma design data into Elementor-compatible tokens. This phase must complete before Elementor pages, templates, containers, or widgets are created.

## Token Model

Create these groups when present in Figma:

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
- Map Elementor's default global roles: Primary, Secondary, Text, and Accent.
- Add additional tokens only when they are reusable and meaningful.
- Preserve raw Figma values in notes when they do not map cleanly.
- Use readable token names that can survive future Elementor edits.
- Do not create a separate token for every one-off value unless fidelity requires it.

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
