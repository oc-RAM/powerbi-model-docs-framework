# Model Overview

## Summary

| Field | Value |
|-------|-------|
| Model Name | Support Operations Analytics |
| Description | Semantic model for tracking support ticket performance, SLA compliance, customer satisfaction, and assignee workload |
| Owner | Reporting Team |
| Last Updated | 2025-03-08 |
| Power BI Service Workspace | Example Production Workspace |
| Data Refresh Frequency | Daily at 06:00 UTC |
| Row-Level Security | No |
| Composite Model | No |

This model provides operational reporting for a support team that handles service requests (tickets). It enables managers and analysts to monitor volume trends, resolution speed, SLA adherence, and team performance. Reports are used by operations managers, team leads, and leadership stakeholders.

## Purpose

The support operations team needs to track how efficiently tickets are handled, whether SLA commitments are being met, and where bottlenecks occur. Before this model, reporting was done in spreadsheets with inconsistent definitions. This model centralizes the data and gives teams one documented place to review support KPIs.

## Audience

- Operations managers - daily monitoring of ticket volume and SLA compliance
- Team leads - assignee workload and performance tracking
- Leadership readers - monthly summary of service quality and customer satisfaction
- Analysts - ad-hoc analysis and trend identification

## Key Metrics

| Metric | Description |
|--------|-------------|
| Total Tickets | Count of all tickets in the selected period |
| SLA Compliance % | Percentage of tickets resolved within their SLA target |
| Avg Resolution Hours | Average time from ticket open to close |
| CSAT Score | Average customer satisfaction rating (1-5 scale) |
| Backlog Count | Number of currently open tickets |
| First Contact Resolution % | Percentage of tickets resolved on first interaction |

## Model Structure Summary

| Category | Count |
|----------|-------|
| Tables | 7 |
| Measures | 12 |
| Calculated Columns | 2 |
| Relationships | 6 |
| Report Pages | 5 |

## Data Sources

| Source | Type | Description |
|--------|------|-------------|
| Ticketing Database | SQL Database | Primary source for ticket records |
| HR System Extract | Excel | Assignee details updated monthly |
| Requester Directory | SharePoint List | Requester information |

## Known Limitations

- Historical data starts from January 2023. Earlier records were not migrated.
- Customer satisfaction scores are only available for tickets where a survey was completed (~60% response rate).
- Assignee information reflects the current state - historical reassignments are not tracked.
- Channel data (email, phone, portal) was not consistently captured before July 2023.

## Related Documents

| Document | Link |
|----------|------|
| Table Inventory | [table-inventory.md](table-inventory.md) |
| Measure Catalog | [measure-catalog.md](measure-catalog.md) |
| Relationship Map | [relationship-map.md](relationship-map.md) |
| KPI Definitions | [kpi-definition.md](kpi-definition.md) |
| Business Glossary | [business-glossary.md](business-glossary.md) |
