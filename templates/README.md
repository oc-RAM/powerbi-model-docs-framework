# Templates

This folder contains 14 reusable markdown templates for documenting Power BI semantic models and reporting projects.

## How to Use

1. Copy the templates you need into your project's documentation folder
2. Fill in the sections relevant to your model
3. Delete any optional sections that do not apply
4. Keep the structure consistent - it makes cross-project navigation easier

You do not need to use every template. Start with the ones that matter most for your project and add others as the documentation matures.

## Template Index

| Template | Purpose |
|----------|---------|
| [model-overview.md](model-overview.md) | High-level summary of the semantic model |
| [source-inventory.md](source-inventory.md) | Data sources feeding the model |
| [table-inventory.md](table-inventory.md) | All tables with type, grain, and row counts |
| [column-dictionary.md](column-dictionary.md) | Column-level definitions and data types |
| [measure-catalog.md](measure-catalog.md) | All measures with DAX, descriptions, and context |
| [relationship-map.md](relationship-map.md) | Relationships between tables |
| [power-query-docs.md](power-query-docs.md) | Power Query transformation logic |
| [report-page-inventory.md](report-page-inventory.md) | Report pages and their purpose |
| [kpi-definition.md](kpi-definition.md) | KPI definitions with targets and owners |
| [business-glossary.md](business-glossary.md) | Shared business terms and definitions |
| [refresh-deployment-notes.md](refresh-deployment-notes.md) | Refresh schedules and deployment details |
| [handover-summary.md](handover-summary.md) | Context for handovers and transitions |
| [issue-decision-log.md](issue-decision-log.md) | Design decisions and open issues |
| [release-notes.md](release-notes.md) | Version history and change log |

## Recommended Starting Set

For a new model, start with these five:

1. **model-overview.md** - establishes context
2. **table-inventory.md** - maps the model structure
3. **measure-catalog.md** - documents the calculations
4. **relationship-map.md** - shows how tables connect
5. **release-notes.md** - tracks changes from day one

Add others as the project grows or as handover, governance, or audit needs arise.

## Conventions

- File names use kebab-case: `column-dictionary.md`
- Section headers use Title Case: `## Data Types`
- Templates include usage notes in blockquotes (`>`) - remove these when filling in
- Optional sections are marked with `<!-- Optional -->` - delete if not needed
