# KPI Definitions

## Summary

| Field | Value |
|-------|-------|
| Model Name | Support Operations Analytics |
| Last Updated | 2025-03-08 |
| Total KPIs Defined | 5 |

## KPIs

| KPI Name | Definition | Measure | Target | Threshold (Red/Amber/Green) | Frequency | Owner | Source of Truth |
|---------|-----------|---------|--------|----------------------------|-----------|-------|-----------------|
| SLA Compliance | Percentage of closed tickets resolved within their SLA target hours | SLA Compliance % | > 90% | Red < 85%, Amber 85-90%, Green > 90% | Weekly | Operations Manager | Service Level Agreement v3.1 |
| Average Resolution Time | Mean hours from ticket creation to resolution | Avg Resolution Hours | < 24 hours | Red > 48h, Amber 24-48h, Green < 24h | Weekly | Operations Manager | Internal target |
| Customer Satisfaction | Average satisfaction score from post-resolution surveys | CSAT Score | > 4.0 / 5.0 | Red < 3.5, Amber 3.5-4.0, Green > 4.0 | Monthly | Service Quality Lead | Customer experience policy |
| Backlog Size | Total number of currently unresolved tickets | Backlog Count | < 500 | Red > 750, Amber 500-750, Green < 500 | Daily | Team Lead | Capacity planning model |
| First Contact Resolution | Percentage of tickets resolved within 1 hour of creation | First Contact Resolution % | > 30% | Red < 20%, Amber 20-30%, Green > 30% | Monthly | Operations Manager | Internal target |

## Detailed KPI Documentation

### SLA Compliance

- **Business Definition**: The percentage of resolved tickets where the actual resolution time was less than or equal to the SLA target defined by the ticket's priority level at creation. Only closed tickets are included.
- **Calculation**: SLA Met Count / Closed Tickets
- **Measure Name**: SLA Compliance %
- **Target**: > 90%
- **Thresholds**:
  - Green: > 90%
  - Amber: 85% - 90%
  - Red: < 85%
- **Review Frequency**: Weekly (operations review), Monthly (executive report)
- **Owner**: Operations Manager
- **Source of Truth**: Service Level Agreement v3.1
- **Caveats**: Tickets cancelled before resolution are excluded. Tickets reopened after closure are not double-counted.
- **History**: Target was 85% prior to 2024-Q3, raised to 90% after process improvements.

### Customer Satisfaction (CSAT)

- **Business Definition**: The average score from post-resolution satisfaction surveys, on a scale of 1 (very dissatisfied) to 5 (very satisfied). Only tickets with a completed survey are included.
- **Calculation**: Average of SatisfactionScore where not blank
- **Measure Name**: CSAT Score
- **Target**: > 4.0
- **Thresholds**:
  - Green: > 4.0
  - Amber: 3.5 - 4.0
  - Red: < 3.5
- **Review Frequency**: Monthly
- **Owner**: Service Quality Lead
- **Source of Truth**: Customer experience policy
- **Caveats**: Survey response rate is approximately 60%. Low response rates may introduce bias - satisfied customers are less likely to respond.
- **History**: Stable target since model inception.

### Backlog Size

- **Business Definition**: The count of all currently open (unresolved) tickets, regardless of when they were created. This represents the real-time workload.
- **Calculation**: Count of FactTicket where IsResolved = FALSE, ignoring date filters
- **Measure Name**: Backlog Count
- **Target**: < 500 tickets
- **Thresholds**:
  - Green: < 500
  - Amber: 500 - 750
  - Red: > 750
- **Review Frequency**: Daily
- **Owner**: Team Lead
- **Source of Truth**: Capacity planning model
- **Caveats**: Includes all priorities. A future improvement may track backlog by priority separately.
- **History**: Target was 1,000 in 2023, reduced to 500 in 2024 after team expansion.

## KPI Change History

| Date | KPI | Change | Reason | Approved By |
|------|-----|--------|--------|------------|
| 2024-07-01 | SLA Compliance | Target raised from 85% to 90% | Process improvements made threshold achievable | Director of Operations |
| 2024-01-15 | Backlog Size | Target reduced from 1,000 to 500 | Team expanded from 80 to 150 assignees | Operations Manager |
