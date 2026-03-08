# Power Query Documentation

> Remove these blockquote instructions when filling in this template.

## Summary

| Field | Value |
|-------|-------|
| Model Name | |
| Last Updated | |
| Total Queries | |
| Queries Loading to Model | |
| Reference / Staging Queries | |

> Document the Power Query (M) transformations applied in this model. Focus on non-trivial logic - filtering, joins, pivots, custom functions, and business rules applied during load.

## Query Index

| Query Name | Loads To | Source | Key Transformations | Notes |
|-----------|----------|--------|---------------------|-------|
| | Table / Reference Only / Staging | | | |
| | | | | |

> **Loads To**: Whether this query loads data into the model ("Table"), is used only as a reference by other queries ("Reference Only"), or is a staging step ("Staging").

## Query Details

### [QueryName]

- **Source**:
- **Loads To**: Table / Reference Only
- **Row Count**: Approximate
- **Description**: What this query does and why

**Key Transformation Steps**:

| Step | Operation | Description |
|------|-----------|-------------|
| 1 | Source | Connects to [source] |
| 2 | FilterRows | Filters to [condition] |
| 3 | RenameColumns | Renames [X] to [Y] |
| 4 | AddColumn | Calculates [column] as [logic] |
| 5 | MergeQueries | Joins with [table] on [key] |

> Document steps that apply business logic, filtering, or structural changes. Skip trivial steps like "Changed Type" unless the type change is non-obvious.

**M Code** (key sections):

<!-- Optional - include if the logic is complex enough to warrant it -->

```powerquery
let
    Source = ...,
    // Key transformation logic here
    Result = ...
in
    Result
```

## Parameters

<!-- Optional -->

> Document any Power Query parameters used in this model.

| Parameter Name | Type | Current Value | Description |
|---------------|------|---------------|-------------|
| | Text / Number / Date | | |

## Custom Functions

<!-- Optional -->

> Document any reusable M functions defined in this model.

| Function Name | Purpose | Parameters | Used By |
|--------------|---------|------------|---------|
| | | | |

## Common Patterns

<!-- Optional -->

> Note any recurring transformation patterns across queries in this model.

- **Date key generation**:
- **Null handling**:
- **Lookup enrichment**:
- **Incremental load logic**:

## Notes

-
