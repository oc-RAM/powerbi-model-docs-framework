# Handover Summary

## Summary

| Field | Value |
|-------|-------|
| Model / Project Name | Support Operations Analytics |
| Handover Date | 2025-03-08 |
| From | Previous maintainer |
| To | Next maintainer |
| Reason | Ownership transition |

## What This Model Does

This semantic model provides operational reporting for a support team handling service tickets. It tracks volume, resolution performance, SLA compliance, customer satisfaction, and assignee workload. Reports are used daily by operations managers and weekly by leadership readers. See [model-overview.md](model-overview.md) for full details.

## Current State

| Area | Status | Notes |
|------|--------|-------|
| Model | Stable | No known bugs. Last structural change was 2025-01-15. |
| Reports | Stable | 5 pages, all functional. Minor formatting improvement requested for Backlog Analysis. |
| Refresh | Working | Daily refresh at 06:00 UTC. Occasional delays when upstream processing runs long. |
| Documentation | Complete | All templates are filled in. This folder contains the full documentation set. |

## Key Files and Locations

| Asset | Location |
|-------|----------|
| .pbix File | Shared document repository path |
| Power BI Workspace | Example Production Workspace |
| Source Data | Ticketing database (SQL), HR extract repository, requester directory list |
| Documentation Folder | This folder |

## Things the Next Maintainer Should Know

1. The HR System Extract is uploaded manually on the 1st of each month. If it is late, `DimAssignee` data will be stale.
2. The `SLA Compliance %` measure only includes closed tickets. Open tickets are excluded because their final resolution time is unknown. If readers ask about that behavior, point them to the business glossary entry.
3. The `Backlog Count` measure uses `ALL(DimDate)` intentionally. It always shows the current open ticket count regardless of the date slicer. This is by design, not a bug.
4. The gateway (`ExampleGateway`) occasionally requires connection re-authentication for repository-based sources. That can cause a failed refresh until the platform support team updates the connection.

## Open Work

| Item | Priority | Status | Notes |
|------|----------|--------|-------|
| Improve Backlog Analysis page layout | Low | Open | Requested by the reporting owner; non-urgent |
| Evaluate incremental refresh | Medium | Open | Should be done when row count exceeds 1M |
| Add CloseDate relationship to DimDate | Low | Open | Would enable time intelligence on close date; requires inactive relationship |

## Regular Maintenance Tasks

| Task | Frequency | Notes |
|------|-----------|-------|
| Monitor daily refresh | Daily | Check Power BI Service for failures |
| Verify HR extract upload | Monthly | Confirm `DimAssignee` row count updated |
| Review SLA targets with the reporting owner | Quarterly | Targets may change |
| Update documentation after changes | As needed | Update relevant template files |

## Key Contacts

| Role | Name | Contact | Notes |
|------|------|---------|-------|
| Business Owner | Operations manager | - | Reviews KPI targets and report changes |
| Data Source Owner (Ticketing) | Data platform team | - | ETL pipeline and database access |
| Data Source Owner (HR) | HR operations | - | Monthly assignee extract |
| Gateway Admin | Platform support team | - | Gateway credentials and availability |

## Documentation Inventory

| Document | Description | Link |
|----------|-------------|------|
| Model Overview | High-level summary | [model-overview.md](model-overview.md) |
| Measure Catalog | All measures with DAX | [measure-catalog.md](measure-catalog.md) |
| Refresh Notes | Schedule and deployment | [refresh-deployment-notes.md](refresh-deployment-notes.md) |
| Issue Log | Decisions and open items | [issue-decision-log.md](issue-decision-log.md) |
| Business Glossary | Term definitions | [business-glossary.md](business-glossary.md) |
| KPI Definitions | Targets and thresholds | [kpi-definition.md](kpi-definition.md) |
