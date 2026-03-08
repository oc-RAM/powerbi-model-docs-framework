# Column Dictionary

> Remove these blockquote instructions when filling in this template.

## Summary

| Field | Value |
|-------|-------|
| Model Name | |
| Last Updated | |
| Total Columns Documented | |

> Document columns for each table. Focus on columns that are important for understanding the model - keys, business fields, calculated columns, and any column with non-obvious meaning. You do not need to document every system-generated or trivially obvious column.

## [TableName]

| Column Name | Data Type | Description | Source Field | Example Values | Notes |
|------------|-----------|-------------|-------------|----------------|-------|
| | Text / Whole Number / Decimal / Date / Boolean / DateTime | | | | |
| | | | | | |

> **Data Type**: The data type as it appears in Power BI (Text, Whole Number, Decimal Number, Date, DateTime, Boolean, etc.).
>
> **Source Field**: The original field name in the source system, if different from the Power BI column name.
>
> **Example Values**: 2-3 representative values to clarify what the column contains.
>
> **Notes**: Any constraints, transformations, default values, or business rules applied to this column.

## Calculated Columns

<!-- Optional -->

> Document any DAX calculated columns. These are often less visible and more prone to being undocumented.

| Table | Column Name | DAX Expression | Description |
|-------|------------|----------------|-------------|
| | | | |

## Column Naming Conventions

<!-- Optional -->

> If this model follows specific naming patterns, document them here for consistency.

| Pattern | Convention | Example |
|---------|-----------|---------|
| Keys | Suffix with `Key` | `CategoryKey` |
| Dates | Suffix with `Date` | `OpenDate`, `CloseDate` |
| Flags | Prefix with `Is` | `IsResolved`, `IsEscalated` |
| Counts | Prefix with `Num` or suffix with `Count` | `NumItems`, `TicketCount` |

## Notes

-
