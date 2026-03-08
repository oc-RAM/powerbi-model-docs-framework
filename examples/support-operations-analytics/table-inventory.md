# Table Inventory

## Summary

| Field | Value |
|-------|-------|
| Model Name | Support Operations Analytics |
| Last Updated | 2025-03-08 |
| Total Tables | 7 |
| Fact Tables | 1 |
| Dimension Tables | 6 |
| Bridge / Mapping Tables | 0 |
| Calculated Tables | 0 |
| Other | 0 |

## Tables

| # | Table Name | Type | Description | Grain | Approx Rows | Source | Key Column(s) | Hidden |
|---|-----------|------|-------------|-------|-------------|--------|---------------|--------|
| 1 | FactTicket | Fact | Support ticket transactions | One row per ticket | 500,000 | Ticketing Database | TicketID | No |
| 2 | DimAssignee | Dimension | Support team members who handle tickets | One row per assignee | 150 | HR System Extract | AssigneeKey | No |
| 3 | DimCategory | Dimension | Ticket classification categories | One row per category | 25 | Ticketing Database | CategoryKey | No |
| 4 | DimPriority | Dimension | Ticket priority levels | One row per priority | 4 | Ticketing Database | PriorityKey | No |
| 5 | DimRequester | Dimension | People or departments that submit tickets | One row per requester | 2,000 | Customer Directory | RequesterKey | No |
| 6 | DimChannel | Dimension | How the ticket was submitted | One row per channel | 5 | Ticketing Database | ChannelKey | No |
| 7 | DimDate | Dimension | Standard date dimension | One row per day | 1,461 | Power Query generated | DateKey | No |

## Fact Tables

### FactTicket

- **Grain**: One row per support ticket
- **Source**: Ticketing Database (dbo.Tickets)
- **Key**: TicketID (unique)
- **Description**: Contains all ticket records with timestamps, resolution data, SLA targets, satisfaction scores, and foreign keys to all dimension tables. This is the only fact table in the model.
- **Approx Rows**: 500,000

## Dimension Tables

### DimAssignee

- **Type**: Type 1 (current state only)
- **Source**: HR System Extract (Assignees.xlsx)
- **Key**: AssigneeKey
- **Description**: Support team members. Includes name, team, role, hire date, and active status. Updated monthly from HR.
- **Approx Rows**: 150

### DimCategory

- **Type**: Static (rarely changes)
- **Source**: Ticketing Database (dbo.Categories)
- **Key**: CategoryKey
- **Description**: Ticket categories such as Hardware, Software, Network, Access, and General Inquiry.
- **Approx Rows**: 25

### DimPriority

- **Type**: Static
- **Source**: Ticketing Database (dbo.Priorities)
- **Key**: PriorityKey
- **Description**: Four priority levels: Critical, High, Medium, Low. Each has a standard SLA target in hours.
- **Approx Rows**: 4

### DimRequester

- **Type**: Type 1 (current state only)
- **Source**: Customer Directory (SharePoint List)
- **Key**: RequesterKey
- **Description**: People or departments that submit support tickets. Includes name, department, and preferred channel.
- **Approx Rows**: 2,000

### DimChannel

- **Type**: Static
- **Source**: Ticketing Database (dbo.Channels)
- **Key**: ChannelKey
- **Description**: Ticket submission channels: Email, Phone, Portal, Chat, Walk-in.
- **Approx Rows**: 5

### DimDate

- **Type**: Generated (Power Query)
- **Source**: Power Query date generation function
- **Key**: DateKey (YYYYMMDD integer format)
- **Description**: Standard date dimension covering 2023-01-01 to 2026-12-31. Includes Year, Quarter, Month, Week, Day of Week, and fiscal period columns.
- **Approx Rows**: 1,461

## Notes

- DimDate is generated entirely in Power Query - no external source dependency.
- DimAssignee uses a surrogate key (AssigneeKey) rather than employee ID, to isolate the model from source system key changes.
- All dimension keys use integer data types for optimal relationship performance.
