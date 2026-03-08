# Table Inventory

> Remove these blockquote instructions when filling in this template.

## Summary

| Field | Value |
|-------|-------|
| Model Name | |
| Last Updated | |
| Total Tables | |
| Fact Tables | |
| Dimension Tables | |
| Bridge / Mapping Tables | |
| Calculated Tables | |
| Other | |

## Tables

| # | Table Name | Type | Description | Grain | Approx Rows | Source | Key Column(s) | Hidden |
|---|-----------|------|-------------|-------|-------------|--------|---------------|--------|
| 1 | | Fact / Dim / Bridge / Calc / Other | | | | | | Yes / No |
| 2 | | | | | | | | |
| 3 | | | | | | | | |

> **Type**: Fact, Dimension, Bridge/Mapping, Calculated Table, Parameter Table, or Other.
>
> **Grain**: What one row represents (e.g., "one ticket", "one day", "one agent-month").
>
> **Source**: Which data source feeds this table. Reference the source-inventory.md entry.
>
> **Key Column(s)**: The primary key or unique identifier column(s) for this table.
>
> **Hidden**: Whether the table is hidden from report authors in the model.

## Fact Tables

> Brief description of each fact table's role and grain.

### [FactTableName]

- **Grain**: One row per...
- **Source**:
- **Key**:
- **Description**:
- **Approx Rows**:

## Dimension Tables

> Brief description of each dimension table.

### [DimTableName]

- **Type**: Type 1 / Type 2 / Slowly changing / Static
- **Source**:
- **Key**:
- **Description**:
- **Approx Rows**:

## Calculated Tables

<!-- Optional -->

> List any DAX-generated calculated tables and their purpose.

| Table Name | DAX Expression | Purpose |
|-----------|----------------|---------|
| | | |

## Notes

> Any additional context - planned table additions, deprecation notes, or structural considerations.

-
