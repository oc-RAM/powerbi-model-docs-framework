# Measure Catalog

## Summary

| Field | Value |
|-------|-------|
| Model Name | Support Operations Analytics |
| Last Updated | 2025-03-08 |
| Total Measures | 12 |

## Measures

### Volume

| Measure Name | DAX Expression | Format | Description | Dependencies | Business Context |
|-------------|----------------|--------|-------------|--------------|------------------|
| Total Tickets | `COUNTROWS(FactTicket)` | #,0 | Count of all tickets in the current filter context | - | Primary volume metric |
| Open Tickets | `CALCULATE(COUNTROWS(FactTicket), FactTicket[IsResolved] = FALSE)` | #,0 | Count of tickets that have not been closed | - | Indicates current workload |
| Closed Tickets | `CALCULATE(COUNTROWS(FactTicket), FactTicket[IsResolved] = TRUE)` | #,0 | Count of resolved tickets | - | Tracks throughput |

### Resolution Performance

| Measure Name | DAX Expression | Format | Description | Dependencies | Business Context |
|-------------|----------------|--------|-------------|--------------|------------------|
| Avg Resolution Hours | `AVERAGE(FactTicket[ResolutionHours])` | #,0.0 | Average hours from ticket open to close | - | Key efficiency metric; lower is better |
| Median Resolution Hours | `MEDIAN(FactTicket[ResolutionHours])` | #,0.0 | Median hours from ticket open to close | - | Less sensitive to outliers than average |

### SLA

| Measure Name | DAX Expression | Format | Description | Dependencies | Business Context |
|-------------|----------------|--------|-------------|--------------|------------------|
| SLA Met Count | `CALCULATE(COUNTROWS(FactTicket), FactTicket[ResolutionHours] <= FactTicket[SLATargetHours], FactTicket[IsResolved] = TRUE)` | #,0 | Tickets resolved within SLA target | - | Numerator for SLA Compliance % |
| SLA Compliance % | `DIVIDE([SLA Met Count], [Closed Tickets], 0)` | 0.0% | Percentage of closed tickets resolved within SLA | SLA Met Count, Closed Tickets | Primary SLA metric; target is 90% |

### Customer Satisfaction

| Measure Name | DAX Expression | Format | Description | Dependencies | Business Context |
|-------------|----------------|--------|-------------|--------------|------------------|
| CSAT Score | `AVERAGE(FactTicket[SatisfactionScore])` | 0.0 | Average satisfaction rating (1-5 scale) | - | Target is 4.0 or higher |
| CSAT Response Rate | `DIVIDE(COUNTROWS(FILTER(FactTicket, NOT(ISBLANK(FactTicket[SatisfactionScore])))), COUNTROWS(FactTicket), 0)` | 0.0% | Percentage of tickets with a satisfaction response | - | Low response rate may bias CSAT Score |

### Backlog

| Measure Name | DAX Expression | Format | Description | Dependencies | Business Context |
|-------------|----------------|--------|-------------|--------------|------------------|
| Backlog Count | `CALCULATE(COUNTROWS(FactTicket), FactTicket[IsResolved] = FALSE, ALL(DimDate))` | #,0 | Total currently open tickets regardless of date filter | - | Measures unresolved workload |

### Productivity

| Measure Name | DAX Expression | Format | Description | Dependencies | Business Context |
|-------------|----------------|--------|-------------|--------------|------------------|
| First Contact Resolution % | `DIVIDE(CALCULATE(COUNTROWS(FactTicket), FactTicket[ResolutionHours] <= 1, FactTicket[IsResolved] = TRUE), [Closed Tickets], 0)` | 0.0% | Percentage of tickets resolved within 1 hour | Closed Tickets | Proxy for first-contact resolution |
| Assignee Utilization | `DIVIDE([Closed Tickets], COUNTROWS(VALUES(DimAssignee[AssigneeKey])), 0)` | #,0.0 | Average closed tickets per assignee | Closed Tickets | Measures team capacity usage |

## Detailed Measure Documentation

### SLA Compliance %

- **Display Folder**: SLA
- **Format String**: 0.0%
- **Description**: The percentage of closed tickets that were resolved within their individual SLA target hours. Each ticket's SLA target is set by its priority level at creation time.
- **DAX**:
  ```dax
  SLA Compliance % =
  DIVIDE(
      [SLA Met Count],
      [Closed Tickets],
      0
  )
  ```
- **Dependencies**: SLA Met Count, Closed Tickets
- **Business Context**: This is the primary SLA metric reported to management. The target is 90%. Dropping below 85% triggers an escalation review.
- **Notes**: Only considers closed tickets. Open tickets are excluded because their final resolution time is unknown.

### Backlog Count

- **Display Folder**: Backlog
- **Format String**: #,0
- **Description**: The total number of currently open (unresolved) tickets. Uses ALL(DimDate) to ignore the date filter, showing the true current backlog regardless of what date range is selected.
- **DAX**:
  ```dax
  Backlog Count =
  CALCULATE(
      COUNTROWS(FactTicket),
      FactTicket[IsResolved] = FALSE,
      ALL(DimDate)
  )
  ```
- **Dependencies**: None
- **Business Context**: Used on the Backlog Analysis page and the Executive Summary. A rising backlog signals capacity problems. Target is to keep backlog below 500 tickets.
- **Notes**: This measure intentionally overrides the date filter to show the current state, not a historical snapshot.

## Measure Naming Conventions

| Pattern | Convention | Example |
|---------|-----------|---------|
| Counts | No prefix | Total Tickets, Open Tickets, Closed Tickets |
| Ratios / Rates | Suffix with `%` or `Rate` | SLA Compliance %, CSAT Response Rate |
| Averages | Prefix with `Avg` or `Median` | Avg Resolution Hours, Median Resolution Hours |
| Intermediate | Descriptive name | SLA Met Count |
