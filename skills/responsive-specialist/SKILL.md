---
name: responsive-specialist
description: Adapt and validate Elementor desktop, tablet, and mobile layouts derived from Figma using responsive controls, container behavior, accessibility, and performance-aware layout decisions.
---

# Responsive Specialist

## Responsibility

Adapt Figma layouts to Elementor responsive behavior across desktop, tablet, and mobile.

## Rules

- Preserve Figma intent, not accidental desktop-only absolute positions.
- Use Elementor responsive controls for spacing, alignment, sizing, direction, order, and visibility where available.
- Avoid duplicating entire sections for responsiveness unless there is no maintainable alternative.
- Prevent text overflow, overlapping widgets, unstable container heights, and layout shifts.
- Ensure containers use responsive flow instead of fixed `width` or `height` values.
- Keep tap targets usable on mobile.
- Preserve semantic order when changing visual order.
- For headers, keep the logo, primary navigation, CTA, and utility items in a predictable semantic order even when the visual layout changes.
- Prefer a single responsive header structure with breakpoint-specific controls; duplicate desktop/mobile headers only when Elementor or the theme cannot express the required behavior cleanly.
- On tablet and mobile, collapse long navigation into the site's existing menu pattern, keep the active CTA reachable, and avoid forcing menu labels into cramped horizontal rows.
- Keep sticky headers compact on scroll and verify they do not cover anchors, admin bars, cookie bars, or first-section content.
- Preserve meaningful logo sizing and aspect ratio; never let the logo, menu toggle, or CTA resize the header unexpectedly.

## Checks

- Desktop layout matches the Figma reference.
- Tablet layout preserves hierarchy, spacing, and readable line lengths.
- Mobile layout stacks predictably, keeps headings readable, and avoids horizontal scroll.
- Containers do not create horizontal scroll at any breakpoint.
- Desktop, tablet, and mobile layouts rely on responsive flow rather than fixed container width or height.
- Any container `max-width` or `min-height` remains intentional, responsive, and valid for each breakpoint.
- Images keep meaningful crop and aspect ratio.
- Buttons and interactive elements remain accessible.
- Header desktop layout keeps nav alignment, logo scale, CTA placement, and sticky state consistent with the reference.
- Header tablet layout avoids squeezed nav items; menu collapse, wrapping, or item hiding is documented in `elementor_mapping.responsive_rules`.
- Header mobile layout keeps the menu toggle visible, tap targets at least 44px where feasible, and no horizontal scroll.
- Header dropdowns/off-canvas menus remain keyboard reachable and do not trap focus unintentionally.
- Header height changes do not create layout shift or obscure page content.

## Output

Update:

- `elementor_mapping.responsive_rules`
- `qa.responsive`
- `qa.accessibility`
- `implementation.warnings`

For header work, include responsive rules for:

- breakpoint behavior for desktop, tablet, and mobile
- logo sizing and container max-width or flow constraints
- navigation display, collapse, wrapping, or hidden items
- menu toggle visibility and interaction pattern
- CTA visibility, order, and tap target
- sticky/header overlap offsets when applicable
