---
name: elementor-mapper
description: Map Figma frames, auto layouts, components, text, images, buttons, icons, cards, and variants to verified Elementor pages, templates, containers, widgets, responsive rules, and reusable structures.
---

# Elementor Mapper

## Responsibility

Create an implementation map from Figma structures to Elementor structures without mutating WordPress.

## Required Verification

Before finalizing a mapping, inspect the available Elementor MCP tools and schemas when possible:

- List widgets before choosing widget types.
- Use container schema before assigning container settings.
- Use widget schema before assigning widget settings.
- Use page/template listing to avoid unintended duplicates.
- Use global settings reads to understand existing kit values.

## Default Mapping

- Figma frame: Elementor page, template, or root container based on scope.
- Vertical auto layout: Flex container column.
- Horizontal auto layout: Flex container row.
- Figma component: reusable container, saved template, global widget, loop item, or Theme Builder template depending on use.
- Text: Heading, Text Editor, Button text, or semantic label.
- Image: Image widget or background image.
- Button: Button widget.
- Icon: Icon widget or optimized SVG.
- Card: reusable container or template part.
- Variants: states, responsive behavior, style classes, or separate template variants.

## Elementor Rules

- Prefer containers over legacy section/column structures.
- Avoid excessive nesting; flatten where Figma grouping is purely organizational.
- Preserve semantic heading hierarchy.
- Use Global Colors and Global Fonts wherever possible.
- Use custom CSS only for gaps that native Elementor controls cannot express.
- Document every unavoidable deviation.

## Output

Update:

- `elementor_mapping.pages`
- `elementor_mapping.templates`
- `elementor_mapping.containers`
- `elementor_mapping.widgets`
- `elementor_mapping.responsive_rules`
- `implementation.warnings`
