# Documenting a New Model

This guide describes a practical workflow for documenting a Power BI semantic model from scratch using the framework templates.

## Before You Start

Gather this information:

- Access to the .pbix file or the Power BI Service dataset
- Knowledge of the data sources and their update schedules
- Familiarity with the key business questions the model answers
- Contact information for the business owner and data source owners

## Recommended Documentation Order

This order builds context progressively - each document builds on the previous.

### Phase 1: Foundation (Day 1)

| Order | Template | Time Estimate | Why First |
|-------|----------|---------------|-----------|
| 1 | model-overview.md | 15-20 min | Establishes context for everything else |
| 2 | table-inventory.md | 20-30 min | Maps the model structure |
| 3 | relationship-map.md | 15-20 min | Shows how tables connect |
| 4 | release-notes.md | 5 min | Creates the first version entry |

After Phase 1, anyone can open the documentation and understand the model's shape and purpose.

### Phase 2: Core Detail (Days 2-3)

| Order | Template | Time Estimate | Why Now |
|-------|----------|---------------|---------|
| 5 | measure-catalog.md | 30-60 min | Most time-consuming but most valuable |
| 6 | source-inventory.md | 15 min | Documents where data comes from |
| 7 | column-dictionary.md | 30-45 min | Focus on key tables first |

After Phase 2, a developer could maintain the model without the original author.

### Phase 3: Business Context (Week 1-2)

| Order | Template | Time Estimate | Why Now |
|-------|----------|---------------|---------|
| 8 | kpi-definition.md | 15-20 min | Defines targets and thresholds |
| 9 | business-glossary.md | 20-30 min | Captures shared vocabulary |
| 10 | report-page-inventory.md | 15-20 min | Documents the report layer |

After Phase 3, the documentation supports governance and handovers.

### Phase 4: Operations and History (Ongoing)

| Order | Template | Time Estimate | Why Now |
|-------|----------|---------------|---------|
| 11 | power-query-docs.md | 20-40 min | Needed when ETL logic is complex |
| 12 | refresh-deployment-notes.md | 15 min | Capture deployment details |
| 13 | handover-summary.md | 15 min | Write before any transition |
| 14 | issue-decision-log.md | Ongoing | Add entries as decisions are made |

## Tips for Each Phase

### Measure Catalog

This is usually the most time-consuming template. Make it easier:

- Export your measure list from Power BI Desktop (External Tools or Performance Analyzer)
- Start with the measures visible on report pages
- Group by display folder
- Document dependencies between measures
- Add business context - "why" is more valuable than "what"

### Column Dictionary

You do not need to document every column. Focus on:

- Primary and foreign key columns
- Columns with non-obvious names
- Calculated columns (these are often undocumented)
- Columns with business rules applied during Power Query

### Business Glossary

Start by listing terms that appear in measure names, KPI cards, and report titles. For each:

- Write a precise definition
- Note who owns the definition
- Note if the term has ever been disputed

## Common Mistakes

- **Trying to document everything in one session.** Spread it over a week. Phase 1 is enough to be useful immediately.
- **Writing descriptions that repeat the name.** "Total Tickets" described as "The total number of tickets" adds no value. Instead: "Count of all ticket records in the selected date range, including both open and resolved."
- **Skipping business context.** Technical documentation is necessary but not sufficient. Always explain why a measure or KPI exists.
- **Not updating documentation after changes.** Set a habit: update docs in the same session as model changes.

## Automation

If your model has many measures or tables, consider:

- Exporting metadata from Power BI Desktop or the Power BI Service to CSV, then using it to pre-fill templates
- Using Claude Code with the `create-model-docs` skill to scaffold the documentation set
- Using the `generate-measure-catalog-entry` skill to document individual measures from DAX expressions

See [claude-code-integration.md](claude-code-integration.md) for details.
