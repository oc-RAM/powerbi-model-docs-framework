# Roadmap

This roadmap reflects the planned direction for the Power BI Model Docs Framework. Items are organized by phase. Timelines are approximate and depend on community interest and contribution.

## Current State (v0.1)

- 14 markdown templates for semantic model documentation
- 1 complete worked example (Support Operations Analytics)
- 8 guides covering usage, adaptation, and maintenance
- Claude Code support with 6 skills
- Project governance and contribution structure

## Phase 1: Template Refinement

- Gather feedback on existing templates from early adopters
- Add optional fields and sections based on real-world usage
- Improve the column dictionary template with clearer data type guidance and common patterns
- Add an RLS (Row-Level Security) documentation template
- Add a data lineage / source-to-target mapping template

## Phase 2: Additional Examples

- Add a second worked example using a different domain (for example, sales analytics, HR reporting, or financial reporting)
- Create a minimal example showing the smallest useful documentation set for a simple model
- Add before/after examples showing how documentation improves over time

## Phase 3: Governance Workflows

- Add a model review checklist template
- Add a documentation review checklist for pull requests
- Create a sample governance workflow for documentation sign-off
- Add a RACI template for documentation ownership

## Phase 4: Tooling and Automation

- Explore metadata extraction helpers that generate draft documentation from semantic model metadata (TMDL, TMSL, or MCP-based)
- Add a validation script that checks a documentation folder for completeness
- Explore GitHub Actions or CI integration for documentation quality checks

## Phase 5: Enterprise and Fabric Adaptation

- Add guidance for documenting Fabric lakehouses and warehouses alongside semantic models
- Add adaptation notes for large-scale enterprise deployments with many models
- Add multi-model documentation patterns (shared dimensions, composite models)
- Explore integration with Microsoft Purview or similar catalog tools

## Phase 6: Community Growth

- Create issue templates for template suggestions and bug reports
- Add a discussion board for framework design questions
- Explore a community gallery of contributed templates and examples

---

Items may shift between phases based on feedback. If you have suggestions, open an issue.
