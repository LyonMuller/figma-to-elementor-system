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
- Do not copy fixed Figma dimensions into Elementor container `width` or `height` settings. Build containers with responsive flow instead: flex direction, gap, padding, alignment, `width: 100%`, breakpoint controls, and `max-width` or `min-height` only when they support the responsive intent.
- Preserve semantic heading hierarchy.
- Use Global Colors and Global Fonts wherever possible.
- Use custom CSS only for gaps that native Elementor controls cannot express.
- Before mapping custom CSS, classify it as page-local or site-wide. Route site-wide header, footer, and global widget CSS to the active theme CSS file or equivalent theme asset pipeline unless project constraints make that impossible.
- Custom CSS must respect global variables/tokens, use `rem`, use CSS Nesting where the project supports it, and avoid `!important`. If selector strength is needed, prefer better scoping, `:where()`, or `:is()` before considering `!important`.
- Document every unavoidable deviation, including any dimension constraint that cannot be expressed without `max-width`, `min-height`, or breakpoint-specific responsive rules.
- Explicitly document any unavoidable `!important` use and why theme CSS or selector scoping could not solve it.

## Output

Update:

- `elementor_mapping.pages`
- `elementor_mapping.templates`
- `elementor_mapping.containers`
- `elementor_mapping.widgets`
- `elementor_mapping.responsive_rules`
- `implementation.warnings`
