---
name: elementor-mapper
description: Map Figma frames, auto layouts, components, text, images, buttons, icons, cards, and variants to verified Elementor pages, templates, containers, widgets, responsive rules, and reusable structures.
---

# Elementor Mapper

## Responsibility

Create an implementation map from Figma structures to Elementor structures without mutating WordPress.

## Required Verification

Before finalizing a mapping, inspect the available Elementor MCP tools and schemas:

- List widgets before choosing widget types.
- Use container schema before assigning container settings.
- Use widget schema before assigning widget settings.
- Use page/template listing to avoid unintended duplicates.
- Read existing Global Colors, Global Fonts, Theme Style, and representative page/template structures.

## Default Mapping

- Figma frame: Elementor page, template, or root container based on scope.
- Figma auto layout: Elementor container only when it controls shared direction, gap, alignment, wrapping, responsive behavior, or semantic grouping.
- Figma group/frame used only for visual organization: flatten into the nearest meaningful Elementor container.
- Figma component: reusable container, saved template, global widget, loop item, or Theme Builder template only when reuse is real and supported by the target Elementor site.
- Text: Heading, Text Editor, Button text, or semantic label.
- Image: Image widget or background image.
- Button: Button widget.
- Icon: Icon widget or optimized SVG.
- Card: one container only when the card needs shared padding, background, border, gap, or responsive grouping.
- Variants: native widget states, responsive controls, or separate template variants. Do not introduce CSS classes as the default variant mechanism.

## Elementor Rules

- Prefer containers over legacy section/column structures.
- Build the smallest tree that preserves semantic sections, shared layout behavior, and responsive control.
- Create a container only for one of these reasons: shared layout behavior, flex direction, gap, alignment, wrapping, responsive behavior, semantic sectioning, reusable structure, or a native Elementor setting that cannot be applied directly to the child widget.
- Do not create containers to visually organize the Navigator, wrap a single widget without a control need, create spacing, mimic CSS, mirror every Figma group, or preserve a desktop-only layer tree.
- Flatten unnecessary nested containers before finalizing `elementor_mapping.containers`.
- Do not copy fixed Figma dimensions into Elementor container `width` or `height` settings. Build containers with responsive flow instead: flex direction, gap, padding, alignment, `width: 100%`, `auto`, native breakpoint controls, and `max-width` or `min-height` only when they support the responsive intent.
- Prefer `rem` for padding, margin, gap, radius, font size, and general spacing when the Elementor control supports unit selection.
- Avoid rigid widths such as fixed pixel values. If a native Elementor control only accepts `px`, document the limitation and do not add CSS as a workaround.
- Preserve semantic heading hierarchy.
- Use only existing Elementor Global Colors and Global Fonts. Do not map raw hex, RGBA, manually sampled colors, invented tokens, or new globals unless the user explicitly approves a global update.
- If a Figma color, font, spacing, or layout detail has no native Elementor/global equivalent, record a divergence in `implementation.warnings` and recommend the closest maintainable option.
- Do not map custom CSS, inline styles, CSS classes, IDs, or external stylesheets as part of the standard plan.
- If custom CSS appears necessary, stop that part of the mapping, record why native Elementor controls are insufficient, and require explicit user approval before including any CSS strategy.
- Do not prioritize pixel-perfect Figma fidelity over an editable Elementor structure.

## Output

Update:

- `elementor_mapping.pages`
- `elementor_mapping.templates`
- `elementor_mapping.containers`
- `elementor_mapping.widgets`
- `elementor_mapping.responsive_rules`
- `implementation.warnings`
