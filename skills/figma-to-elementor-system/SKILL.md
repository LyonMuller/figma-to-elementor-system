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
- Never publish Elementor content unless the user explicitly authorizes publishing in the current conversation.
- Default all Elementor page/template creation to draft or equivalent non-public status.
- Prefer native Elementor controls, Global Colors, Global Fonts, Theme Style, Containers/Flexbox, widgets, templates, and reusable structures before custom HTML/CSS.
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
6. Normalize the Elementor design system in `design_system`.
7. Map Figma structures to Elementor global settings, pages, templates, containers, widgets, and responsive rules in `elementor_mapping`.
8. Optimize and organize assets before Elementor construction.
9. Create or update Elementor global colors, global typography, theme style, drafts, templates, containers, widgets, and responsive settings through verified Elementor MCP tools.
10. Validate desktop, tablet, and mobile behavior.
11. Run QA against visual fidelity, design system consistency, Elementor best practices, accessibility, performance, semantic headings, and style duplication.
12. Generate final HTML reports using templates in `../../templates/`.

## Blocking Conditions

Stop and report in HTML when:

- Figma MCP cannot read the requested design or node.
- Elementor MCP cannot read global settings or create drafts.
- Required Elementor capabilities are unavailable, such as Pro-only templates for a requested Theme Builder workflow.
- The requested action would publish content without explicit authorization.
- Widget schemas or container settings cannot be verified for the intended build.
- The Figma frame is too large and cannot be decomposed with metadata and child-node fetches.

## Output

At completion, provide:

- Created or updated Elementor item IDs, titles, and statuses.
- Design system summary.
- Asset summary.
- QA summary with blockers and warnings.
- Path to the final HTML report.
- Any manual checks required in WordPress/Elementor.
