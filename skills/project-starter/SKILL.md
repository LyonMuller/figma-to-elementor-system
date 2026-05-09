---
name: project-starter
description: Start a new Figma to Elementor conversion project. Use when the user wants to begin, scope, intake, prepare, or validate a Figma to Elementor project before running the full workflow through Figma MCP and Elementor MCP.
---

# Project Starter

## Purpose

Use this skill to turn an initial project request into a clear, safe, actionable Figma to Elementor conversion scope.

This skill runs before design analysis, design system normalization, Elementor mapping, or Elementor draft creation. Its job is to collect missing inputs, validate obvious blockers, choose conservative defaults, and prepare the handoff to `../figma-to-elementor-system/SKILL.md`.

## Hard Rules

- Do not create or update Elementor content from this skill.
- Do not read private credentials, auth headers, application passwords, tokens, or `.env` values.
- Do not publish anything. If the user does not explicitly authorize publishing, record `draft` as the publication default.
- Do not invent Figma node IDs, target WordPress sites, Elementor capabilities, MCP tools, or project constraints.
- Prefer asking for missing product intent over guessing when the answer changes scope, publication, target site, or deliverables.
- Keep the output short enough to be reused as the starting brief for the main workflow.

## Required Intake

Collect or derive:

- Figma source: URL, file key, selected frame, node ID, or explicit design scope.
- Target WordPress/Elementor site or environment.
- Project scope: `design_system`, `page`, `template`, or `full_site`.
- Publication preference. Default to `draft` when not explicit.
- Elementor constraints: free/pro availability, theme builder needs, dynamic tags, reusable templates, custom widgets, or existing globals.
- Delivery expectations: draft page/template IDs, design system summary, assets, QA report, final HTML report, or implementation plan only.
- Quality constraints: responsive breakpoints, accessibility, SEO, performance, tracking, analytics, multilingual, forms, WooCommerce, or animation needs.

## Startup Workflow

1. Restate the requested outcome in one sentence.
2. Extract known inputs from the user request and active environment.
3. Identify missing inputs that block the workflow.
4. Validate whether Figma MCP and Elementor MCP appear available before promising implementation.
5. Set conservative defaults:
   - publication: `draft`;
   - scope: `page` when a single frame/page is provided;
   - custom CSS: avoid unless required;
   - assets: optimize before Elementor construction when media is present;
   - documentation: generate HTML reports.
6. Flag risks early, especially missing MCP access, unknown target site, Pro-only Elementor requirements, very large Figma frames, unclear responsive behavior, or publishing requests.
7. Produce a project brief and pass it to `../figma-to-elementor-system/SKILL.md`.

## Output

Provide a concise project brief with:

- project name or working title;
- Figma source;
- target site/environment;
- scope;
- publication status;
- known constraints;
- missing inputs or blockers;
- selected defaults;
- next skill to run.

If required inputs are missing, stop after the brief and ask only for the missing information needed to continue safely.
