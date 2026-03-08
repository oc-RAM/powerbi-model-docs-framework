# Source Inventory

## Summary

| Field | Value |
|-------|-------|
| Model Name | Support Operations Analytics |
| Last Updated | 2025-03-08 |
| Total Sources | 3 |

## Sources

| # | Source Name | Source Type | Connection | Schema / Object | Description | Refresh Method | Owner |
|---|------------|-------------|------------|-----------------|-------------|----------------|-------|
| 1 | Ticketing Database | SQL Database | On-premises gateway | dbo.Tickets, dbo.Categories, dbo.Priorities | Primary ticket data with categories and priorities | Full extract daily | Data platform team |
| 2 | HR System Extract | Excel Workbook | Shared repository folder | Assignees.xlsx | Assignee names, teams, and roles | Manual upload monthly | HR operations |
| 3 | Requester Directory | SharePoint List | Shared list service | Requesters list | Requester names, departments, and contact channels | Full extract daily | Service operations |

## Source Dependencies

| Dependency | Description |
|------------|-------------|
| Ticketing Database must be available before 06:00 UTC | Refresh depends on overnight ETL completing by 05:30 UTC |
| HR extract must be uploaded by 1st of each month | Stale assignee data affects team-level reporting |

## Access and Credentials

| Source | Auth Method | Access Managed By |
|--------|-------------|-------------------|
| Ticketing Database | Automation account | Data platform team |
| HR System Extract | OAuth | HR operations |
| Requester Directory | OAuth | Service operations |

## Data Freshness

| Source | Update Frequency | Typical Lag |
|--------|-----------------|-------------|
| Ticketing Database | Daily (overnight ETL) | ~6 hours |
| HR System Extract | Monthly (manual) | Up to 30 days |
| Requester Directory | Daily (automatic sync) | ~12 hours |

## Notes

- The ticketing database includes a `LastModifiedDate` column that could support incremental refresh in the future. The example currently uses a full extract because row volume is still moderate (~500K records).
- The HR extract was originally a CSV but was migrated to Excel in 2024 for easier manual editing.
