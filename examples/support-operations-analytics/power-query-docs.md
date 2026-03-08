# Power Query Documentation

## Summary

| Field | Value |
|-------|-------|
| Model Name | Support Operations Analytics |
| Last Updated | 2025-03-08 |
| Total Queries | 9 |
| Queries Loading to Model | 7 |
| Reference / Staging Queries | 2 |

## Query Index

| Query Name | Loads To | Source | Key Transformations | Notes |
|-----------|----------|--------|---------------------|-------|
| FactTicket | Table | Ticketing Database | Key mapping, calculated columns, date key generation | Main fact query |
| DimAssignee | Table | HR System Extract | Surrogate key generation, status flag | Monthly update |
| DimCategory | Table | Ticketing Database | Rename columns, add group | Static reference |
| DimPriority | Table | Ticketing Database | Rename columns, add SLA defaults | Static reference |
| DimRequester | Table | Customer Directory | Surrogate key generation, trim names | Daily update |
| DimChannel | Table | Ticketing Database | Rename columns | Static reference |
| DimDate | Table | Generated | Full date dimension generation | No external source |
| StagingAssigneeLookup | Reference Only | HR System Extract | Maps EmployeeID to AssigneeKey | Used by FactTicket |
| StagingRequesterLookup | Reference Only | Customer Directory | Maps email to RequesterKey | Used by FactTicket |

## Query Details

### FactTicket

- **Source**: Ticketing Database (dbo.Tickets)
- **Loads To**: Table
- **Row Count**: ~500,000
- **Description**: Loads ticket records and applies key mappings, date key generation, and a resolution hours calculation.

**Key Transformation Steps**:

| Step | Operation | Description |
|------|-----------|-------------|
| 1 | Source | Connects to dbo.Tickets via SQL query |
| 2 | FilterRows | Removes tickets with status "Cancelled" |
| 3 | MergeQueries | Joins with StagingAssigneeLookup on EmployeeID to get AssigneeKey |
| 4 | MergeQueries | Joins with StagingRequesterLookup on RequesterEmail to get RequesterKey |
| 5 | AddColumn | Calculates ResolutionHours as duration between CreatedDate and ResolvedDate |
| 6 | AddColumn | Calculates IsResolved as `ResolvedDate <> null` |
| 7 | AddColumn | Generates OpenDateKey as `Year * 10000 + Month * 100 + Day` |
| 8 | SelectColumns | Keeps only model columns, drops staging fields |
| 9 | ChangeTypes | Sets final data types |

### DimDate

- **Source**: Generated in Power Query
- **Loads To**: Table
- **Row Count**: 1,461
- **Description**: Generates a date dimension from 2023-01-01 to 2026-12-31 with standard calendar attributes.

**Key Transformation Steps**:

| Step | Operation | Description |
|------|-----------|-------------|
| 1 | GenerateDateList | Creates a list of dates from start to end |
| 2 | ConvertToTable | Converts the list to a single-column table |
| 3 | AddColumns | Adds Year, Quarter, MonthNumber, MonthName, WeekNumber, DayOfWeek |
| 4 | AddColumn | Generates DateKey as YYYYMMDD integer |
| 5 | AddColumn | Calculates IsWeekday flag |

### DimAssignee

- **Source**: HR System Extract (Assignees.xlsx)
- **Loads To**: Table
- **Row Count**: ~150
- **Description**: Loads assignee information from the monthly HR export. Generates surrogate keys and maps the status field to a boolean.

**Key Transformation Steps**:

| Step | Operation | Description |
|------|-----------|-------------|
| 1 | Source | Opens Assignees.xlsx from SharePoint folder |
| 2 | PromoteHeaders | Uses first row as headers |
| 3 | AddIndex | Generates AssigneeKey as an index starting at 1 |
| 4 | AddColumn | Maps Status ("Active"/"Inactive") to IsActive boolean |
| 5 | RenameColumns | Renames FullName to AssigneeName, StartDate to HireDate |

## Common Patterns

- **Date key generation**: All date keys use YYYYMMDD integer format, calculated as `Year * 10000 + Month * 100 + Day`
- **Null handling**: Null dates (e.g., CloseDate for open tickets) are preserved as null, not replaced with a default value
- **Lookup enrichment**: FactTicket uses two staging queries as lookup tables to map source system IDs to model surrogate keys
- **Surrogate keys**: DimAssignee and DimRequester use index-based surrogate keys to decouple from source system identifiers

## Notes

- No Power Query parameters are currently used. A future improvement could parameterize the date range for DimDate.
- No custom M functions are defined. The date generation logic could be extracted into a reusable function if additional date dimensions are needed.
