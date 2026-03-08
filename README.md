# Power BI Model Docs Framework

A reusable markdown framework for documenting Power BI semantic models and reporting assets. It provides a consistent structure for model context, tables, measures, relationships, refresh details, and handover notes without requiring any specific tool or platform.

## Who It Is For

- Power BI developers documenting their own models
- BI analysts maintaining shared reporting assets
- Analytics engineers working across multiple semantic models
- Consultants delivering models and reports to clients or internal teams
- Reporting teams that need traceability, governance, and faster handovers

## Minimum Starter Set

If you are starting from scratch, begin with these five files:

- `model-overview.md`
- `table-inventory.md`
- `measure-catalog.md`
- `relationship-map.md`
- `release-notes.md`

That set is enough to explain what the model is for, how it is structured, what it calculates, how tables connect, and how the model has changed over time.

## Concrete Example

Example: a support operations model with one fact table and six dimensions.

1. Document the model purpose and audience in `model-overview.md`.
2. List `FactTicket`, `DimAssignee`, and the other tables in `table-inventory.md`.
3. Capture measures such as `Total Tickets` and `SLA Compliance %` in `measure-catalog.md`.
4. Record the active `FactTicket[OpenDateKey] -> DimDate[DateKey]` relationship in `relationship-map.md`.
5. Add an initial `v1.0 - Initial documentation` entry in `release-notes.md`.

The worked example in [examples/support-operations-analytics/](examples/support-operations-analytics/) shows the full set filled in end to end.

## What This Framework Includes

- 14 reusable markdown templates covering model overview, tables, columns, measures, relationships, Power Query, reports, KPIs, business glossary, refresh/deployment, handovers, decisions, and release notes
- A complete worked example using a generic Support Operations Analytics model
- 8 practical guides covering setup, maintenance, adaptation, and examples
- Optional Claude Code support through project instructions and reusable skills

The framework is plain markdown. It works with any editor, any repository host, and any workflow.

## Repository Structure

```text
powerbi-model-docs-framework/
|-- templates/
|   |-- model-overview.md
|   |-- source-inventory.md
|   |-- table-inventory.md
|   |-- column-dictionary.md
|   |-- measure-catalog.md
|   |-- relationship-map.md
|   |-- power-query-docs.md
|   |-- report-page-inventory.md
|   |-- kpi-definition.md
|   |-- business-glossary.md
|   |-- refresh-deployment-notes.md
|   |-- handover-summary.md
|   |-- issue-decision-log.md
|   `-- release-notes.md
|-- examples/
|   `-- support-operations-analytics/
|-- guides/
|   |-- getting-started.md
|   |-- documenting-a-new-model.md
|   |-- keeping-docs-updated.md
|   |-- using-the-examples.md
|   |-- adapting-the-framework.md
|   |-- claude-code-integration.md
|   |-- best-practices.md
|   `-- maintaining-the-framework.md
|-- .claude/
|   `-- skills/
|-- CLAUDE.md
|-- CONTRIBUTING.md
|-- CODE_OF_CONDUCT.md
|-- CHANGELOG.md
|-- ROADMAP.md
|-- PROJECT_SCOPE.md
`-- LICENSE
```

## Quick Start

1. Clone or download this repository.
2. Copy the templates you need into your project's documentation folder.
3. Start with the minimum starter set.
4. Fill in the templates and remove the instructional blockquotes.
5. Add more templates as the model and reporting estate become more complex.

See [guides/getting-started.md](guides/getting-started.md) for a detailed walkthrough.

## Templates

| Template | Purpose |
|----------|---------|
| [model-overview](templates/model-overview.md) | High-level summary of the semantic model |
| [source-inventory](templates/source-inventory.md) | Data sources feeding the model |
| [table-inventory](templates/table-inventory.md) | All tables with type, grain, and row counts |
| [column-dictionary](templates/column-dictionary.md) | Column-level definitions and data types |
| [measure-catalog](templates/measure-catalog.md) | All measures with DAX, descriptions, and business context |
| [relationship-map](templates/relationship-map.md) | Table relationships and cardinality |
| [power-query-docs](templates/power-query-docs.md) | Power Query transformation logic |
| [report-page-inventory](templates/report-page-inventory.md) | Report pages and their purpose |
| [kpi-definition](templates/kpi-definition.md) | KPI definitions with targets and thresholds |
| [business-glossary](templates/business-glossary.md) | Shared business terms and definitions |
| [refresh-deployment-notes](templates/refresh-deployment-notes.md) | Refresh schedules and deployment details |
| [handover-summary](templates/handover-summary.md) | Context for team transitions and handovers |
| [issue-decision-log](templates/issue-decision-log.md) | Design decisions and open issues |
| [release-notes](templates/release-notes.md) | Version history and change log |

## Example

The [examples/support-operations-analytics/](examples/support-operations-analytics/) folder contains every template filled in for a fictional support ticket reporting model. It demonstrates:

- A star schema with 1 fact table and 6 dimensions
- 12 measures covering volume, SLA, satisfaction, backlog, and productivity
- 5 KPIs with targets and thresholds
- A business glossary with 14 defined terms
- A complete decision log and release history

Use it as a reference for structure and level of detail.

## Use Cases

- New model setup
- Existing model documentation audit
- Team handover
- Governance and traceability
- Consulting delivery
- Analyst and developer onboarding

## Claude Code Support

If you use [Claude Code](https://claude.ai/claude-code), this repository includes:

- A project-level `CLAUDE.md` with repo context, style rules, and public-safety guidance
- 6 reusable skills for common documentation workflows

| Skill | Purpose |
|-------|---------|
| `create-model-docs` | Scaffold a full documentation set from templates |
| `review-documentation` | Review docs against framework standards and flag gaps |
| `generate-measure-catalog-entry` | Create a measure entry from a DAX expression |
| `update-release-notes` | Append a formatted release entry |
| `validate-completeness` | Check for missing or incomplete templates |
| `create-template-from-pattern` | Turn a recurring pattern into a new template |

Claude Code support is optional. The framework is fully usable without it. See [guides/claude-code-integration.md](guides/claude-code-integration.md) for setup details.

## AI-Assisted Documentation Workflows

This framework is designed to work well with AI-assisted development tools such as Claude Code.

Claude can help automate parts of the documentation workflow, including:

• generating measure catalog entries from DAX expressions  
• reviewing model documentation for completeness  
• scaffolding documentation templates for new semantic models  
• validating that required documentation files exist in a project  

The repository includes example Claude Code skills that demonstrate how AI can support consistent analytics documentation while keeping humans in control of the documentation process.

The goal is to combine structured documentation practices with AI-assisted workflows to make maintaining BI model documentation easier and more reliable.

## Contributing

Contributions are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

Good first contributions:

- Improve template field descriptions
- Add an example for a different domain
- Write a guide for a specific documentation workflow
- Fix typos or broken links

## Roadmap

See [ROADMAP.md](ROADMAP.md) for the full plan. Near-term items include:

- RLS documentation template
- Data lineage / source-to-target mapping template
- Additional worked examples for different domains
- Model review checklist
- Metadata extraction helpers

## License

MIT. See [LICENSE](LICENSE).
