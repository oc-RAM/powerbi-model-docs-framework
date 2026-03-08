# Release Notes

## Summary

| Field | Value |
|-------|-------|
| Model / Project Name | Support Operations Analytics |
| Last Updated | 2025-03-08 |

## Releases

### v1.4 - Backlog and Productivity Measures

**Released**: 2025-01-15
**Released By**: Developer

**Changes**:

- Added Backlog Count measure with ALL(DimDate) override for real-time view
- Added First Contact Resolution % measure
- Added Assignee Utilization measure
- Created Backlog Analysis report page

**Impact**:

- New report page available to all users
- Backlog Count intentionally ignores date slicer - documented in business glossary

**Notes**:

- Backlog Analysis page layout is functional but may be refined in a future update

---

### v1.3 - SLA Target Update

**Released**: 2024-07-01
**Released By**: Developer

**Changes**:

- Updated SLA Compliance target from 85% to 90%
- Updated conditional formatting thresholds on Executive Summary KPI cards
- Updated KPI definition documentation

**Impact**:

- SLA Compliance KPI card thresholds changed: Green > 90% (was > 85%), Amber 85-90% (was 80-85%), Red < 85% (was < 80%)
- Historical data is not affected - thresholds are applied at display time

---

### v1.2 - CSAT Response Rate

**Released**: 2024-06-01
**Released By**: Developer

**Changes**:

- Added CSAT Response Rate measure
- Added response rate indicator next to CSAT Score on Executive Summary page

**Impact**:

- Users can now see the survey response rate alongside the CSAT score to assess reliability

---

### v1.1 - Channel Data Cleanup

**Released**: 2024-03-15
**Released By**: Developer

**Changes**:

- Added Power Query step to map pre-July 2023 null channel values to "Unknown"
- Added DimChannel table and relationship
- Added Channel slicer to Ticket Trends page

**Impact**:

- Channel analysis now available. Pre-July 2023 data shows as "Unknown" channel.

---

### v1.0 - Initial Release

**Released**: 2023-06-15
**Released By**: Developer

**Changes**:

- Initial model with FactTicket, DimAssignee, DimCategory, DimPriority, DimRequester, DimDate
- 8 core measures: Total Tickets, Open Tickets, Closed Tickets, Avg Resolution Hours, Median Resolution Hours, SLA Met Count, SLA Compliance %, CSAT Score
- 4 report pages: Executive Summary, Ticket Trends, SLA Performance, Assignee Scorecard

**Impact**:

- Replaced previous Excel-based reporting
- First version published to Power BI Service

## Versioning Conventions

| Convention | Description |
|-----------|-------------|
| Major (1.0 -> 2.0) | Breaking changes - renamed measures, removed tables, changed key definitions |
| Minor (1.0 -> 1.1) | New measures, new report pages, non-breaking additions |
| Patch (1.1 -> 1.1.1) | Bug fixes, formatting corrections, documentation updates |
