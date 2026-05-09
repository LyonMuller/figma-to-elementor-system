---
name: html-documentation-writer
description: Generate valid HTML documentation and reports for Figma to Elementor workflows, including design system reports, conversion plans, implementation reports, QA reports, final reports, and technical decisions.
---

# HTML Documentation Writer

## Responsibility

Generate all operational documentation and final reports as valid HTML.

## Rules

- Use Markdown only where Codex requires it, such as `SKILL.md`.
- Write reports with semantic HTML: `header`, `main`, `section`, `table`, `ol`, `ul`, and clear headings.
- Escape user-provided values before embedding them in HTML.
- Do not include credentials, tokens, application passwords, auth headers, private endpoints, or large raw payloads.
- Include timestamps, scope, source Figma node, target site, actions, warnings, QA issues, and next steps.
- Link relative documentation files when possible.

## Templates

Use:

- `../../templates/design-system-report.html`
- `../../templates/conversion-plan.html`
- `../../templates/implementation-report.html`
- `../../templates/qa-report.html`
- `../../templates/final-report.html`

## Output

Produce:

- Design system report.
- Conversion plan.
- Implementation report.
- QA report.
- Final report.
- Technical-decision appendix when assumptions or environment dependencies matter.
