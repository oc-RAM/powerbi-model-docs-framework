# Source Inventory

> Remove these blockquote instructions when filling in this template.

## Summary

| Field | Value |
|-------|-------|
| Model Name | |
| Last Updated | |
| Total Sources | |

> List all data sources that feed into this semantic model. Include both primary and reference/lookup sources.

## Sources

| # | Source Name | Source Type | Connection | Schema / Object | Description | Refresh Method | Owner |
|---|------------|-------------|------------|-----------------|-------------|----------------|-------|
| 1 | | SQL Database / Excel / SharePoint / API / Dataflow / Other | | | | Full / Incremental / Manual | |
| 2 | | | | | | | |
| 3 | | | | | | | |

> **Source Type**: The kind of data source (SQL Server, Azure SQL, Excel workbook, SharePoint list, Dataflow, REST API, CSV, etc.)
>
> **Connection**: Connection string summary or gateway name. Do not include credentials or sensitive connection details.
>
> **Schema / Object**: Database schema, table name, file path, or API endpoint.
>
> **Refresh Method**: How the data is loaded - full extract, incremental load, manual paste, etc.

## Source Dependencies

> Note any dependencies between sources, such as lookup tables that must be refreshed before fact tables, or staging dataflows that feed this model.

| Dependency | Description |
|------------|-------------|
| | |

## Access and Credentials

> Do NOT include actual credentials, tokens, or passwords here. Only note what type of authentication is used and who manages access.

| Source | Auth Method | Access Managed By |
|--------|-------------|-------------------|
| | Service Account / OAuth / API Key / Windows Auth | |

## Data Freshness

> How current is the data from each source

| Source | Update Frequency | Typical Lag |
|--------|-----------------|-------------|
| | Daily / Hourly / Real-time / Manual | |

## Notes

> Any additional context about the sources - known quality issues, planned migrations, deprecation notices, etc.

-
