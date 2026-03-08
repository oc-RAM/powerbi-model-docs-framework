# Getting Started

This guide walks you through using the Power BI Model Docs Framework for the first time.

## Prerequisites

- A Power BI semantic model you want to document
- A folder or repository where you will store the documentation
- A text editor that handles markdown

## Step 1: Copy the Templates

Copy the files from the `templates/` folder into your project's documentation folder. You can copy all 14 or start with just the essentials.

**Recommended starting set:**

```text
your-project/
|-- model-overview.md
|-- table-inventory.md
|-- measure-catalog.md
|-- relationship-map.md
`-- release-notes.md
```

These five cover the most critical documentation needs. Add others as your project matures.

## Step 2: Fill in the Model Overview

Start with `model-overview.md`. This file anchors everything else. Fill in:

- Model name and description
- Owner and refresh schedule
- Purpose and audience
- Key metrics (your top 3-5 measures)
- Model structure counts (tables, measures, relationships)
- Known limitations

A good model overview can be written in 15-20 minutes if you know the model well.

## Step 3: Document the Tables

Open `table-inventory.md` and list every table in the model. For each table:

- Identify whether it is a fact, dimension, bridge, or calculated table
- Write a one-line description
- Note the grain (what one row represents)
- Include approximate row count
- Identify key columns

## Step 4: Document the Measures

Open `measure-catalog.md` and list your measures. Group them by display folder or business area. For each measure:

- Include the full DAX expression
- Describe what it calculates in plain language
- Note dependencies on other measures
- Add business context: why does this measure exist

Start with the measures that appear on report pages. Document internal or helper measures later.

## Step 5: Document Relationships

Open `relationship-map.md` and list all relationships. For each:

- Identify the from and to tables and columns
- Note cardinality and cross-filter direction
- Flag any bidirectional or inactive relationships

If you can, include a simple text diagram of the schema shape.

## Step 6: Start the Release Notes

Open `release-notes.md` and create the first entry. Even if you are documenting an existing model, create a `v1.0 - Initial documentation` entry that captures the model's current state.

## What to Do Next

After the initial five files:

1. Add `source-inventory.md` if data sources are non-obvious.
2. Add `column-dictionary.md` for tables with many columns or non-obvious field names.
3. Add `kpi-definition.md` if your model tracks KPIs with targets and thresholds.
4. Add `business-glossary.md` if terms are interpreted differently across teams.
5. Add `power-query-docs.md` if there is complex transformation logic.

See [documenting-a-new-model.md](documenting-a-new-model.md) for a more detailed workflow.

## Tips

- Do not try to document everything at once. Start with what matters most.
- Focus on information that would help someone unfamiliar with the model understand it.
- Remove the blockquote instructions from templates after filling them in.
- Keep entries concise. A table with 10 well-described rows is more useful than 50 sparse rows.
- Update documentation when you make model changes, not weeks later.
