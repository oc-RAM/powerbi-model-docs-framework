# Column Dictionary

## Summary

| Field | Value |
|-------|-------|
| Model Name | Support Operations Analytics |
| Last Updated | 2025-03-08 |
| Total Columns Documented | 38 |

## FactTicket

| Column Name | Data Type | Description | Source Field | Example Values | Notes |
|------------|-----------|-------------|-------------|----------------|-------|
| TicketID | Whole Number | Unique ticket identifier | dbo.Tickets.TicketID | 100234, 100235 | Primary key |
| OpenDate | Date | Date the ticket was created | dbo.Tickets.CreatedDate | 2024-06-15 | Used for time intelligence |
| CloseDate | Date | Date the ticket was resolved and closed | dbo.Tickets.ResolvedDate | 2024-06-17 | Null if still open |
| SLATargetHours | Decimal Number | Target resolution time per SLA agreement | dbo.Tickets.SLAHours | 8, 24, 72 | Inherited from priority at creation |
| ResolutionHours | Decimal Number | Actual hours from open to close | Calculated in PQ | 6.5, 23.1 | Null if still open |
| CategoryKey | Whole Number | Foreign key to DimCategory | dbo.Tickets.CategoryID | 1, 2, 3 | |
| PriorityKey | Whole Number | Foreign key to DimPriority | dbo.Tickets.PriorityID | 1, 2, 3, 4 | |
| AssigneeKey | Whole Number | Foreign key to DimAssignee | Mapped via lookup | 10, 11, 12 | Mapped from EmployeeID in PQ |
| RequesterKey | Whole Number | Foreign key to DimRequester | Mapped via lookup | 501, 502 | Mapped from requester email in PQ |
| ChannelKey | Whole Number | Foreign key to DimChannel | dbo.Tickets.ChannelID | 1, 2, 3 | |
| SatisfactionScore | Whole Number | Customer satisfaction rating | dbo.Tickets.CSATRating | 1, 2, 3, 4, 5 | Null if no survey response |
| IsResolved | Boolean | Whether the ticket has been closed | Calculated in PQ | TRUE, FALSE | Derived from CloseDate |
| OpenDateKey | Whole Number | Foreign key to DimDate for open date | Calculated in PQ | 20240615 | YYYYMMDD format |

## DimAssignee

| Column Name | Data Type | Description | Source Field | Example Values | Notes |
|------------|-----------|-------------|-------------|----------------|-------|
| AssigneeKey | Whole Number | Surrogate key | Generated in PQ | 10, 11 | Primary key |
| AssigneeName | Text | Full name of the support agent | Assignees.xlsx.FullName | Alex Johnson | |
| Team | Text | Team the assignee belongs to | Assignees.xlsx.Team | Tier 1, Tier 2, Specialists | |
| Role | Text | Job role or title | Assignees.xlsx.Role | Analyst, Senior Analyst, Lead | |
| HireDate | Date | Date the assignee was hired | Assignees.xlsx.StartDate | 2022-03-15 | |
| IsActive | Boolean | Whether the assignee is currently active | Assignees.xlsx.Status | TRUE, FALSE | Inactive = left the team |

## DimCategory

| Column Name | Data Type | Description | Source Field | Example Values | Notes |
|------------|-----------|-------------|-------------|----------------|-------|
| CategoryKey | Whole Number | Surrogate key | dbo.Categories.CategoryID | 1, 2, 3 | Primary key |
| CategoryName | Text | Ticket category label | dbo.Categories.Name | Hardware, Software, Network, Access | |
| CategoryGroup | Text | High-level grouping | dbo.Categories.GroupName | Technical, Administrative | |

## DimPriority

| Column Name | Data Type | Description | Source Field | Example Values | Notes |
|------------|-----------|-------------|-------------|----------------|-------|
| PriorityKey | Whole Number | Surrogate key | dbo.Priorities.PriorityID | 1, 2, 3, 4 | Primary key |
| PriorityName | Text | Priority level label | dbo.Priorities.Name | Critical, High, Medium, Low | |
| SortOrder | Whole Number | Display sort order | dbo.Priorities.SortOrder | 1, 2, 3, 4 | 1 = Critical |
| DefaultSLAHours | Whole Number | Default SLA target for this priority | dbo.Priorities.SLAHours | 4, 8, 24, 72 | |

## DimRequester

| Column Name | Data Type | Description | Source Field | Example Values | Notes |
|------------|-----------|-------------|-------------|----------------|-------|
| RequesterKey | Whole Number | Surrogate key | Generated in PQ | 501, 502 | Primary key |
| RequesterName | Text | Name of the person or department | SharePoint.DisplayName | Maria Santos, IT Department | |
| Department | Text | Organizational department | SharePoint.Department | Finance, Marketing, IT | |
| PreferredChannel | Text | Preferred contact method | SharePoint.Channel | Email, Phone | |

## DimChannel

| Column Name | Data Type | Description | Source Field | Example Values | Notes |
|------------|-----------|-------------|-------------|----------------|-------|
| ChannelKey | Whole Number | Surrogate key | dbo.Channels.ChannelID | 1, 2, 3, 4, 5 | Primary key |
| ChannelName | Text | Ticket submission channel | dbo.Channels.Name | Email, Phone, Portal, Chat, Walk-in | |

## DimDate

| Column Name | Data Type | Description | Source Field | Example Values | Notes |
|------------|-----------|-------------|-------------|----------------|-------|
| DateKey | Whole Number | Surrogate key (YYYYMMDD) | Generated | 20240615 | Primary key |
| Date | Date | Calendar date | Generated | 2024-06-15 | |
| Year | Whole Number | Calendar year | Generated | 2024 | |
| Quarter | Text | Calendar quarter | Generated | Q1, Q2, Q3, Q4 | |
| MonthNumber | Whole Number | Month number (1-12) | Generated | 6 | |
| MonthName | Text | Month name | Generated | June | |
| WeekNumber | Whole Number | ISO week number | Generated | 24 | |
| DayOfWeek | Text | Day name | Generated | Monday | |
| IsWeekday | Boolean | Whether the date is a weekday | Generated | TRUE, FALSE | |

## Column Naming Conventions

| Pattern | Convention | Example |
|---------|-----------|---------|
| Keys | Suffix with `Key` | `CategoryKey`, `AssigneeKey` |
| Dates | Suffix with `Date` | `OpenDate`, `CloseDate`, `HireDate` |
| Flags | Prefix with `Is` | `IsResolved`, `IsActive`, `IsWeekday` |
| Names | Suffix with `Name` | `CategoryName`, `ChannelName` |
| Sort columns | Prefix with `Sort` or suffix with `Order` | `SortOrder` |
