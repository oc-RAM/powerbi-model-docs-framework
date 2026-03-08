# Best Practices

Practical guidance for getting the most value from the framework.

## Writing Documentation

### Be Specific

Bad: "This measure calculates the total."
Good: "Count of all ticket records in the selected date range, including both open and resolved tickets. Excludes cancelled tickets."

### Write for the Reader Who Does Not Know the Model

Assume the reader is a competent Power BI developer joining the project for the first time. They understand Power BI but know nothing about this specific model, its business context, or its history.

### Business Context Matters More Than Technical Descriptions

For every measure, answer: "Why does this measure exist What decision does it support" A DAX expression tells you **what** it calculates. Business context tells you **why** anyone cares.

### Use Consistent Language

If the model calls it a "Ticket", use "Ticket" everywhere - not "Incident" in one file and "Case" in another. The business glossary exists to enforce this.

### Keep It Current

Stale documentation is worse than no documentation because it creates false confidence. Update docs in the same session as model changes. Use the "Last Updated" date on each file as a staleness indicator.

## Template Usage

### Start Small, Add Incrementally

Do not try to fill in all 14 templates on day one. Start with the five essentials (model overview, table inventory, measure catalog, relationship map, release notes) and add more as the project matures.

### Delete What You Do Not Need

If a template section does not apply to your model, delete it. An empty section adds noise. A deleted section adds nothing.

### Fill In Examples, Not Just Headers

A table with headers but no rows is not documentation. If you add a template, fill in at least the most important rows. Placeholder text like "TBD" should be resolved within a week.

## Measure Catalog

### Document Dependencies

When a measure references other measures, list them. This is critical for understanding impact when changes are made.

```
SLA Compliance % depends on: SLA Met Count, Closed Tickets
```

### Group by Business Area

Group measures by what they mean to the business (Volume, SLA, Satisfaction), not by technical category (CALCULATE measures, SUMX measures). Business users will search by topic, not by DAX function.

### Include the Full DAX

Abbreviated DAX is not useful. Include the complete expression. If it is too long for a table cell, use the detailed documentation format with a code block.

## Relationship Map

### Flag Non-Standard Relationships

Standard relationships (many-to-one, single-direction) need minimal notes. Spend your documentation effort on:

- Bidirectional cross-filters (why do they exist)
- Inactive relationships (what measures use them)
- Many-to-many relationships (what are the consequences)
- Role-playing dimensions (which path is active)

## KPI Definitions

### Always Include Thresholds

A KPI without a target is just a metric. Document:

- The target value
- The RAG thresholds (Red / Amber / Green)
- Who set the target
- When it was last reviewed

### Track Target Changes

When KPI targets change, update the KPI definition file **and** add an entry to the KPI Change History section. This prevents confusion when historical reports show different performance relative to current thresholds.

## Business Glossary

### Add Terms Proactively

Do not wait for confusion. If you notice a term that different stakeholders might interpret differently, add it to the glossary before it becomes a problem.

### Document Disputes

When a term's definition is debated and resolved, record the dispute and resolution. This prevents the same debate from recurring with new team members.

## File Organization

### One Model, One Folder

Keep all documentation for a single model in one folder. Do not scatter templates across multiple directories.

### Use Links Between Files

Templates include `Related Documents` sections for a reason. Link between files so readers can navigate from a model overview to the measure catalog to the KPI definitions without searching.

### Do Not Duplicate Content

If information belongs in the measure catalog, do not also put it in the model overview. Use a link instead. Duplication causes drift.
