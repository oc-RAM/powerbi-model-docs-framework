# Issue and Decision Log

## Summary

| Field | Value |
|-------|-------|
| Model / Project Name | Support Operations Analytics |
| Last Updated | 2025-03-08 |

## Decisions

| # | Date | Decision | Context | Alternatives Considered | Decided By |
|---|------|----------|---------|------------------------|-----------|
| D1 | 2023-06-15 | Use calendar hours for resolution time, not business hours | SLA agreement defines targets in calendar hours. Calculating business hours would add complexity without aligning to the contract. | Business hours calculation with configurable work schedule | Operations manager |
| D2 | 2023-07-01 | Use surrogate keys for DimAssignee and DimRequester | Source system IDs could change during migrations. Surrogate keys isolate the model from source key changes. | Use source system IDs directly | Developer |
| D3 | 2023-09-10 | Use OpenDate as the active DimDate relationship, not CloseDate | Most analysis focuses on when tickets were created. CloseDate analysis can use `USERELATIONSHIP` if needed later. | CloseDate as active, or dual date tables | Operations manager + developer |
| D4 | 2024-01-20 | Exclude cancelled tickets from the model | Cancelled tickets inflate volume counts and distort SLA metrics. They represent requests withdrawn before any work began. | Include with a status filter, or separate cancelled count | Operations manager |
| D5 | 2024-04-10 | Define First Contact Resolution as resolved within 1 hour | Source data lacks sub-hour granularity. 1 hour is the smallest reliable threshold. | 30-minute threshold, or use a different proxy metric | Operations manager |
| D6 | 2024-07-01 | Raise SLA Compliance target from 85% to 90% | Process improvements and team expansion made the previous target too easy. | Keep at 85%, or raise to 95% | Operations lead |

## Open Issues

| # | Date Raised | Issue | Priority | Assigned To | Status | Notes |
|---|------------|-------|----------|-------------|--------|-------|
| I1 | 2025-01-15 | Backlog Analysis page layout needs improvement | Low | Next maintainer | Open | Reporting owner requested better grouping of aging categories |
| I2 | 2025-02-01 | Evaluate incremental refresh feasibility | Medium | Next maintainer | Open | Row count approaching threshold where full refresh may become slow |
| I3 | 2025-02-20 | Add inactive relationship for CloseDate to DimDate | Low | Unassigned | Open | Would enable "tickets closed this week" analysis without workarounds |

## Resolved Issues

| # | Date Raised | Issue | Resolution | Resolved Date | Resolved By |
|---|------------|-------|------------|---------------|------------|
| I4 | 2024-08-01 | Refresh timeout during bulk import | Increased timeout from 30 to 60 minutes | 2024-08-03 | Developer |
| I5 | 2024-05-15 | CSAT Score unreliable for months with low survey responses | Added `CSAT Response Rate` so users can see sample size | 2024-06-01 | Developer |
| I6 | 2024-03-10 | Channel data inconsistent before July 2023 | Documented as a known limitation. Pre-July 2023 channel data marked as `Unknown` in Power Query | 2024-03-15 | Developer |

## Architecture Decisions

### Star Schema with Single Fact Table (D2, D3)

- **Date**: 2023-06-15
- **Context**: The model needed to support volume, SLA, satisfaction, and assignee analysis from a single ticket dataset.
- **Decision**: Classic star schema with `FactTicket` at the center and six dimension tables. Single-direction cross-filters only. No bidirectional relationships.
- **Consequences**: Simple, performant, and easy to maintain. Limits some advanced analysis, but those cases can be handled with measures rather than structural changes.
- **Status**: Active
