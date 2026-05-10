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
- Read existing global settings before applying any style mapping.
- Prefer updates over duplicate creation when the target item is clearly identifiable.
- Do not delete page content, templates, or widgets unless explicitly authorized.
- Do not use Pro-only tools unless Elementor Pro capability is verified.
- Do not add custom code snippets or unfiltered HTML unless the user explicitly approves the risk.
- Do not apply custom CSS, inline CSS, style classes, IDs, or external stylesheets unless the user explicitly approved that exception in the current conversation.
- Do not create new Global Colors or Global Fonts, or apply raw color/font values, unless the user explicitly approved that global update.

## Preferred Tool Order

Use actual tool availability from the active Elementor MCP server. Expected tools may include:

1. `get-global-settings`
2. Page/template structure reads for representative clean Elementor layouts
3. Widget and container schema reads
4. `list-pages`
5. `list-templates`
6. `create-page`
7. `update-page-settings`
8. `add-container`
9. `add-widget`
10. Widget-specific helpers such as `add-heading`, `add-text-editor`, `add-image`, `add-button`, and `add-icon`
11. `build-page` for approved declarative page structures
12. `update-global-colors` or `update-global-typography` only after explicit user approval
13. `save-as-template` or `create-theme-template` when appropriate

## Build Rules

- Confirm that every mapped color and font references an existing Elementor global before page construction.
- Add root containers with semantic `html_tag` values where supported, but require each nested container to have a documented layout, responsive, semantic, reuse, or native-control reason.
- Reject containers used only as visual wrappers, one-widget wrappers, spacers, Figma layer mirrors, or CSS substitutes.
- Reject fixed `width` or `height` settings on containers before creating or updating them. Replace them with native responsive controls such as flex settings, gap, padding, alignment, `width: 100%`, `auto`, breakpoint-specific values, `max-width`, or `min-height` where appropriate.
- Do not apply rigid container dimensions only to match a desktop Figma frame pixel-for-pixel.
- Prefer `rem` for padding, margin, gap, border radius, font size, and spacing wherever the Elementor control supports unit selection.
- Document any Elementor control that only accepts `px`; do not use custom CSS to bypass the control.
- Reject hardcoded hex, RGBA, manually sampled color values, invented tokens, or local font settings when an existing Elementor global is required.
- Add widgets with verified widget settings.
- If the mapping needs custom CSS and approval is missing, skip that styling operation, record a warning, and leave a manual decision for the user.
- If the user approved custom CSS, keep it outside the standard build path, scope it narrowly, document why native Elementor controls failed, and record it in `implementation.warnings`.
- Use batch update only when each operation is known and reversible.
- Record all created, updated, skipped, and warning items.

## Output

Update:

- `implementation.actions`
- `implementation.created_items`
- `implementation.updated_items`
- `implementation.skipped_items`
- `implementation.warnings`
