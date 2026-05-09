---
name: qa-reviewer
description: Review Figma to Elementor conversion quality, including visual fidelity, global tokens, container structure, headings, accessibility, responsiveness, performance, duplicate styles, and custom CSS risk.
---

# QA Reviewer

## Responsibility

Perform final review and decide whether the conversion is acceptable, acceptable with warnings, or blocked.

## Review Areas

- Visual fidelity to Figma screenshots.
- Consistent use of Elementor Global Colors.
- Consistent use of Elementor Global Fonts.
- Design system token completeness.
- Container/Flexbox structure quality.
- Heading semantics and document outline.
- Basic accessibility: contrast, alt text, labels, focus, tap targets.
- Responsive behavior across desktop, tablet, and mobile.
- Performance: asset weight, DOM depth, unnecessary scripts, layout shifts.
- Duplicate styles and excessive custom CSS.

## Blocking Findings

Block completion when:

- The design system was skipped.
- Page/template content was published without authorization.
- Major visual hierarchy is wrong.
- Critical content is inaccessible or hidden.
- Mobile layout has overlap or horizontal scroll.
- Elementor build relies on unverified widget schema.
- Custom CSS or code snippets introduce unnecessary risk.

## Output

Update:

- `qa.visual`
- `qa.responsive`
- `qa.accessibility`
- `qa.performance`
- `qa.elementor_best_practices`
- `qa.open_issues`
