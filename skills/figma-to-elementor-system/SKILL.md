---
name: figma-to-elementor-system
description: Orchestrate a complete Figma to Elementor workflow. Use when the user wants to convert Figma files, frames, pages, templates, components, or design systems into Elementor using Figma MCP and Elementor MCP.
---

# Figma to Elementor System

## Purpose

Use this skill to transform Figma designs into Elementor-ready design systems, pages, templates, containers, widgets, assets, responsive rules, QA findings, and HTML reports.

This skill is intentionally light. It coordinates specialized subskills and keeps the workflow ordered, auditable, and safe.

For new projects or unclear requests, start with `../project-starter/SKILL.md` before running the full conversion workflow.

## Hard Rules

- Build the design system before creating or updating pages, templates, containers, or widgets.
- Consult Elementor MCP for existing Global Colors, Global Fonts, Theme Style, page/template structure, widget availability, container schema, and widget schemas before mapping or building.
- Never publish Elementor content unless the user explicitly authorizes publishing in the current conversation.
- Default all Elementor page/template creation to draft or equivalent non-public status.
- Use native Elementor controls, existing Global Colors, existing Global Fonts, Theme Style, Containers/Flexbox, widgets, templates, and reusable structures as the default implementation surface.
- Do not use custom CSS, inline CSS, CSS classes, IDs, custom code snippets, or external CSS as a standard layout or styling solution.
- Use custom CSS only after explicit user approval in the current conversation. If Elementor native controls cannot express a Figma detail, record the divergence and ask for approval instead of inventing CSS.
- Do not create new Global Colors or Global Fonts from Figma values during normal conversion. Recommend additions when needed, but map only to existing Elementor globals unless the user explicitly authorizes global updates.
- Create the smallest Elementor structure that preserves semantic grouping, responsive control, and maintainability.
- Prefer `rem` for spacing, typography, radius, and gaps when Elementor controls allow unit selection. Document controls that only accept `px`; do not add CSS to bypass that limitation.
- Do not apply hardcoded colors, hex/RGBA values, invented tokens, rigid widths, or fixed dimensions only to match a desktop Figma frame.
- Do not invent MCP tools, Elementor setting names, widget schemas, Figma node IDs, or unpublished APIs. Inspect available tools and schemas first.
- Do not copy secrets, application passwords, MCP auth headers, tokens, or private endpoints into plugin files or reports.
- Produce operational documentation and final reports in valid HTML. Markdown is allowed only for `SKILL.md`.

## Required Inputs

Collect or derive:

- Figma URL, file key, node ID, selected frame, or explicit scope.
- Target WordPress/Elementor site.
- Scope: `design_system`, `page`, `template`, or `full_site`.
- Publication preference. If not explicit, use draft.
- Any constraints around Elementor Pro, theme templates, dynamic tags, assets, accessibility, SEO, tracking, or performance.

## Subskill Order

Run the workflow in this order. Before each phase, read the relevant subskill instructions:

1. `../project-starter/SKILL.md` for new projects, unclear requests, or missing intake details
2. `../figma-analyzer/SKILL.md`
3. `../design-system-builder/SKILL.md`
4. `../elementor-mapper/SKILL.md`
5. `../asset-optimizer/SKILL.md` when assets are present
6. `../elementor-builder/SKILL.md`
7. `../responsive-specialist/SKILL.md`
8. `../qa-reviewer/SKILL.md`
9. `../html-documentation-writer/SKILL.md`

## Workflow

1. Use the project starter when the request needs intake, scoping, defaults, or blocker discovery.
2. Validate that Figma MCP and Elementor MCP are configured in the active environment. If a server or tool is missing, stop implementation and generate an HTML blocking report.
3. Parse Figma URLs carefully. Convert URL node IDs like `1-2` to MCP node IDs like `1:2` when the active Figma tool requires colon format.
4. Initialize the internal JSON contract from `../../contracts/internal-data-contract.json`.
5. Analyze the Figma source and store design context, screenshot references, variables, styles, metadata, components, layout patterns, and assets in `figma_analysis`.
6. Read existing Elementor globals, schemas, widgets, and representative page/template structures through Elementor MCP.
7. Normalize the Figma design system against existing Elementor globals in `design_system`; record unmatched Figma values as divergences or recommendations.
8. Map visual hierarchy into the smallest maintainable Elementor tree in `elementor_mapping`; separate structure, content, and style before creating containers.
9. Optimize and organize assets before Elementor construction.
10. Create or update Elementor drafts, templates, containers, widgets, and responsive settings through verified Elementor MCP tools.
11. Validate desktop, tablet, and mobile behavior.
12. Run QA against visual fidelity, design system consistency, Elementor best practices, accessibility, performance, semantic headings, custom CSS approval, global color/font usage, and style duplication.
13. Generate final HTML reports using templates in `../../templates/`.

## Blocking Conditions

Stop and report in HTML when:

- Figma MCP cannot read the requested design or node.
- Elementor MCP cannot read global settings or create drafts.
- Required Elementor capabilities are unavailable, such as Pro-only templates for a requested Theme Builder workflow.
- The requested action would publish content without explicit authorization.
- Widget schemas or container settings cannot be verified for the intended build.
- Existing Elementor Global Colors or Global Fonts cannot be read.
- The requested visual result requires custom CSS and the user has not explicitly approved that exception.
- The Figma frame is too large and cannot be decomposed with metadata and child-node fetches.

## Output

At completion, provide:

- Created or updated Elementor item IDs, titles, and statuses.
- Design system summary.
- Asset summary.
- QA summary with blockers and warnings.
- Path to the final HTML report.
- Any manual checks required in WordPress/Elementor.
