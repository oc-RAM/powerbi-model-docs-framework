# Project Scope

## What This Framework Is

A structured, reusable documentation framework for Power BI semantic models and reporting projects. It provides markdown templates, practical guides, and a worked example that help teams document their models consistently.

The framework is designed for teams that need to:

- Document semantic models for handover, onboarding, or audit purposes
- Standardize how measures, tables, relationships, and Power Query logic are described
- Maintain a living record of KPI definitions, business terms, and design decisions
- Reduce the cost of context-switching between projects by using a common structure

## Who It Is For

- Power BI developers documenting their own models
- BI analysts maintaining shared reporting assets
- Analytics engineers working across multiple semantic models
- Consultants handing off dashboards and data models to clients or internal teams
- Reporting teams that need governance, traceability, and handover documentation

## What It Covers

- **14 markdown templates** covering model overview, tables, columns, measures, relationships, Power Query, reports, KPIs, business glossary, refresh/deployment, handovers, issues/decisions, and release notes
- **A complete worked example** using a generic support operations analytics model
- **8 practical guides** for getting started, documenting new models, keeping docs current, adapting the framework, and maintaining it as an open-source project
- **Claude Code integration** with project-level instructions and reusable skills for common documentation workflows

## Non-goals

This framework is explicitly **not** the following:

- **Not a Power BI theme pack or visual design system.** It does not include report themes, color palettes, or layout templates.
- **Not a DAX tutorial or learning course.** It documents measures but does not teach DAX from scratch.
- **Not a metadata extraction tool.** It does not automatically pull table definitions or measure lists from .pbix files. Automated extraction is a roadmap aspiration, not a current feature.
- **Not tied to any single company's workflow.** The templates and conventions are generic. Teams should adapt them to their own standards.
- **Not a replacement for enterprise governance tooling.** Tools like Microsoft Purview, Collibra, or Atlan serve different purposes at a different scale. This framework is complementary - it provides lightweight, file-based documentation that works in any repository without requiring additional infrastructure.
- **Not a data catalog.** It documents individual models, not an organization-wide inventory of all datasets and reports.

## Design Principles

1. **Useful without any specific tool.** The framework is plain markdown. It works with any editor, any repository host, and any workflow.
2. **Structure over volume.** A well-organized set of short, focused documents is better than a single long specification.
3. **Practical over theoretical.** Templates include concrete field descriptions and examples, not abstract instructions.
4. **Generic over proprietary.** All content is designed for broad reuse. No company-specific conventions are baked in.
5. **Maintainable over comprehensive.** The framework should be easy to keep current. If a template creates maintenance burden without clear value, it should not exist.
