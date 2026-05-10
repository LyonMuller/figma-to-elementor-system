---
name: elementor-builder
description: Implement verified Elementor mappings through Elementor MCP by creating or updating global colors, global fonts, theme style, draft pages, templates, containers, widgets, and reusable structures.
---

# Elementor Builder

## Responsibility

Execute the approved Elementor mapping through verified Elementor MCP tools.

## Safety Rules

- Never publish without explicit authorization in the current conversation.
- Create pages and templates as drafts by default.
- Read existing global settings before updating them.
- Prefer updates over duplicate creation when the target item is clearly identifiable.
- Do not delete page content, templates, or widgets unless explicitly authorized.
- Do not use Pro-only tools unless Elementor Pro capability is verified.
- Do not add custom code snippets or unfiltered HTML unless the user explicitly approves the risk.

## Preferred Tool Order

Use actual tool availability from the active Elementor MCP server. Expected tools may include:

1. `get-global-settings`
2. `update-global-colors`
3. `update-global-typography`
4. `list-pages`
5. `list-templates`
6. `create-page`
7. `update-page-settings`
8. `add-container`
9. `add-widget`
10. Widget-specific helpers such as `add-heading`, `add-text-editor`, `add-image`, `add-button`, and `add-icon`
11. `build-page` for approved declarative page structures
12. `save-as-template` or `create-theme-template` when appropriate

## Build Rules

- Apply global colors and fonts before page construction.
- Add root containers with semantic `html_tag` values where supported.
- Reject fixed `width` or `height` settings on containers before creating or updating them. Replace them with responsive controls such as flex settings, gap, padding, alignment, `width: 100%`, breakpoint-specific values, `max-width`, or `min-height` where appropriate.
- Do not apply rigid container dimensions only to match a desktop Figma frame pixel-for-pixel.
- Add widgets with verified widget settings.
- Use batch update only when each operation is known and reversible.
- Record all created, updated, skipped, and warning items.

## Output

Update:

- `implementation.actions`
- `implementation.created_items`
- `implementation.updated_items`
- `implementation.skipped_items`
- `implementation.warnings`
