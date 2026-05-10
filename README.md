# Figma to Elementor System

A Codex plugin for converting Figma designs into Elementor-ready design systems, draft pages, templates, reusable containers, widgets, optimized assets, responsive rules, QA findings, and final HTML reports.

This repository is a workflow package. It does not bundle Figma, WordPress, Elementor, credentials, private endpoints, or MCP server configuration.

## When to use it

Use this plugin when you need a structured Figma to Elementor workflow that can:

- analyze Figma files, frames, variables, styles, components, screenshots, and assets;
- normalize design decisions into an Elementor-compatible design system;
- map Figma structures to Elementor globals, containers, widgets, pages, and templates;
- create or update Elementor drafts through verified MCP tools;
- review responsive behavior, accessibility, performance, design fidelity, and Elementor implementation quality;
- generate operational HTML documentation and QA reports.

## Workflow overview

The system is intentionally phase-based:

1. Start the project brief and confirm scope, defaults, missing inputs, and blockers.
2. Validate the requested Figma scope and target WordPress/Elementor site.
3. Confirm that Figma MCP and Elementor MCP tools are available in the active environment.
4. Analyze the Figma source and capture design context, variables, metadata, screenshots, layout patterns, and assets.
5. Build the Elementor-compatible design system before page or template construction.
6. Map the design to Elementor global settings, pages, templates, containers, widgets, and responsive rules.
7. Optimize assets when the design requires exported media.
8. Create or update Elementor content as drafts unless the user explicitly authorizes publishing.
9. Validate desktop, tablet, and mobile behavior.
10. Run QA and generate HTML reports.

## Starting a project

Use the `project-starter` skill first when beginning a new conversion, when the scope is unclear, or when the target environment has not been confirmed.

Example starter prompt:

```text
Use the project-starter skill to prepare a Figma to Elementor conversion.

Figma URL: <url>
Target WordPress/Elementor site: <site or environment>
Scope: design_system | page | template | full_site
Publication: draft only
Constraints:
- use Elementor globals where possible
- avoid custom CSS unless necessary
- optimize assets
- validate desktop, tablet, and mobile
- generate final HTML report
```

After the brief is complete, continue with the `figma-to-elementor-system` skill.

## Requirements

- Codex plugin support.
- Figma MCP configured in the active environment.
- Elementor MCP configured for the target WordPress site.
- Access to the relevant Figma file, frame, node, or selection.
- Permission to create or update Elementor drafts on the target site.

MCP servers, site credentials, auth headers, application passwords, tokens, and private endpoints must stay outside this repository.

## Repository structure

- [`.codex-plugin/plugin.json`](.codex-plugin/plugin.json): Codex plugin manifest.
- [`skills/`](skills/): orchestrator and specialized workflow skills.
- [`docs/index.html`](docs/index.html): operational documentation index.
- [`contracts/internal-data-contract.json`](contracts/internal-data-contract.json): internal JSON contract shared across workflow phases.
- [`examples/`](examples/): example HTML workflow outputs.
- [`templates/`](templates/): HTML report templates.
- [`README.html`](README.html): lightweight HTML entrypoint kept for plugin and LLM-oriented workflows.

## Skills

The main orchestrator is [`skills/figma-to-elementor-system/SKILL.md`](skills/figma-to-elementor-system/SKILL.md). It coordinates these focused skills:

- `project-starter`
- `figma-analyzer`
- `design-system-builder`
- `elementor-mapper`
- `asset-optimizer`
- `elementor-builder`
- `responsive-specialist`
- `qa-reviewer`
- `html-documentation-writer`

Read the orchestrator first, then follow the subskill order defined there.

## Context-specific skills

This plugin includes the core skills required for the Figma to Elementor workflow, but agents may use additional installed skills when the task context requires specialized support.

Use extra skills only when they materially improve the result, such as:

- design critique, UI auditing, or accessibility review beyond the bundled QA checklist;
- image generation, asset editing, or media optimization workflows not covered by the local asset skill;
- spreadsheet, document, presentation, or reporting workflows requested as part of a handoff;
- browser automation or visual regression checks for a live local or staging page;
- project-specific WordPress, Elementor, performance, SEO, analytics, or security guidance.

External skills should be selected from the active agent environment first. If the required capability is missing, use [skills.sh](https://skills.sh/) as a discovery source for reusable agent skills, then install or activate only the skill that matches the current need.

Do not use external skills to bypass the safety rules, MCP validation, draft-first publishing policy, or verified Elementor/Figma contracts defined by this plugin.

## Safety rules

- Never publish Elementor content unless the user explicitly authorizes publishing in the current conversation.
- Default created or updated Elementor pages and templates to draft or equivalent non-public status.
- Do not store secrets, credentials, MCP auth data, private endpoints, tokens, or application passwords in plugin files or generated reports.
- Do not invent MCP tools, Elementor widget schemas, setting names, Figma node IDs, or unpublished APIs. Inspect the active environment first.
- Prefer native Elementor controls, Global Colors, Global Fonts, Theme Style, Containers/Flexbox, widgets, templates, and reusable structures before custom HTML or CSS.
- For header, footer, and global widget styling used across the site, prefer the active theme CSS file or equivalent theme asset pipeline before Elementor custom CSS.
- Use custom CSS only when a native control cannot express the requirement; respect global variables/tokens, use `rem`, use CSS Nesting where the project supports it, and avoid `!important` unless the need is documented.

## Documentation format

GitHub should render this `README.md` as the human-friendly project entrypoint.

The HTML files in [`docs/`](docs/), [`examples/`](examples/), [`templates/`](templates/), and [`README.html`](README.html) are kept intentionally. They serve as operational documentation and structured outputs for agents, LLM workflows, QA reports, and handoff artifacts.

## License

MIT.
