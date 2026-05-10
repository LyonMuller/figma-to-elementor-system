---
name: asset-optimizer
description: Export, name, organize, and optimize Figma images, SVGs, icons, logos, backgrounds, and illustrations for Elementor and WordPress media workflows.
---

# Asset Optimizer

## Responsibility

Prepare Figma assets for WordPress and Elementor while preserving quality, accessibility, naming clarity, and performance.

## Rules

- Prefer SVG for icons and simple vector marks when safe.
- Preserve raster dimensions needed for visual fidelity, but avoid oversized images.
- Name assets with stable, descriptive, lowercase hyphenated filenames.
- Track original Figma node, intended Elementor usage, alt text, and optimization notes.
- Do not replace real Figma assets with placeholders.
- Do not import new icon packages when Figma provides the source asset.
- Avoid embedding large base64 assets in reports or settings.
- Keep logos and critical brand assets visually faithful.

## Elementor Usage

- Use Image widgets for content images.
- Use background images only when the image is decorative or structurally tied to an already justified container.
- Do not create an extra container only to hold a background image when an Image widget or existing semantic container is more maintainable.
- Do not use CSS classes, inline CSS, or external CSS to position assets without explicit user approval.
- Use Icon widgets or uploaded SVG icons for icons.
- Add alt text for meaningful images and mark decorative imagery as decorative where Elementor supports it.

## Output

Update:

- `figma_analysis.assets`
- `elementor_mapping.widgets`
- `implementation.actions`
- `implementation.warnings`
