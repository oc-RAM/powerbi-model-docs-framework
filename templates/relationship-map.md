# Relationship Map

> Remove these blockquote instructions when filling in this template.

## Summary

| Field | Value |
|-------|-------|
| Model Name | |
| Last Updated | |
| Total Relationships | |
| Active Relationships | |
| Inactive Relationships | |

## Relationships

| # | From Table | From Column | To Table | To Column | Cardinality | Cross-filter Direction | Active | Notes |
|---|-----------|-------------|----------|-----------|-------------|----------------------|--------|-------|
| 1 | | | | | Many-to-One / One-to-One / Many-to-Many | Single / Both | Yes / No | |
| 2 | | | | | | | | |
| 3 | | | | | | | | |

> **Cardinality**: Many-to-One (most common for fact-to-dim), One-to-One, or Many-to-Many.
>
> **Cross-filter Direction**: Single (default, from dimension to fact) or Both (bidirectional). Note bidirectional filters - they can cause performance issues and unexpected behavior.
>
> **Active**: Whether this relationship is the active path. Only one active relationship can exist between any two tables. Inactive relationships require `USERELATIONSHIP()` in DAX.

## Relationship Diagram

<!-- Optional -->

> If you have a text-based or ASCII representation of the star/snowflake schema, include it here. Alternatively, describe the topology.

```text
                    DimDate
                      |
DimCategory -- FactTable -- DimAssignee
                      |
                  DimPriority
```

> For complex models, consider referencing an exported diagram image stored alongside this file.

## Inactive Relationships

<!-- Optional -->

> Document any inactive relationships and when they are used.

| From | To | Purpose | Used By (Measure) |
|------|----|---------|--------------------|
| | | | |

## Bidirectional Filters

<!-- Optional -->

> Document any bidirectional cross-filter relationships and the reason they exist.

| From | To | Reason |
|------|----|---------|
| | | |

## Role-Playing Dimensions

<!-- Optional -->

> If a single dimension table connects to a fact table through multiple columns (for example, `DimDate` connected via `OpenDate` and `CloseDate`), document the pattern here.

| Dimension | Fact Table | Columns | Active Relationship |
|-----------|-----------|---------|---------------------|
| | | | |

## Notes

-
