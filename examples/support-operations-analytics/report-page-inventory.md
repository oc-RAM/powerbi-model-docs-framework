# Report Page Inventory

## Summary

| Field | Value |
|-------|-------|
| Report Name | Support Operations Dashboard |
| Model Name | Support Operations Analytics |
| Last Updated | 2025-03-08 |
| Total Pages | 5 |
| Published To | Example Production Workspace |

## Pages

| # | Page Name | Purpose | Audience | Key Visuals | Hidden | Notes |
|---|----------|---------|----------|-------------|--------|-------|
| 1 | Executive Summary | High-level KPI overview and trends | Executives, Managers | KPI cards, trend line, donut chart | No | Landing page |
| 2 | Ticket Trends | Volume analysis over time by category and channel | Analysts, Managers | Stacked bar chart, line chart, matrix | No | |
| 3 | SLA Performance | SLA compliance tracking by priority and team | Managers, Team Leads | Gauge, clustered bar, heat map | No | |
| 4 | Assignee Scorecard | Individual and team performance metrics | Team Leads | Table, bar chart, KPI cards | No | |
| 5 | Backlog Analysis | Current open ticket analysis and aging | Managers, Analysts | Table, bar chart, treemap | No | |

## Page Details

### Executive Summary

- **Purpose**: Provides a single-screen overview of support operations health. Designed for stakeholders who need a quick status check without drilling into details.
- **Audience**: Executives, operations managers
- **Key Visuals**:
  - KPI cards: Total Tickets, SLA Compliance %, Avg Resolution Hours, CSAT Score, Backlog Count
  - Line chart: Total Tickets trend by month (last 12 months)
  - Donut chart: Tickets by priority distribution
  - Bar chart: Top 5 categories by volume
- **Filters / Slicers**: Date range slicer (default: last 30 days), Priority slicer
- **Drillthrough**: No
- **Notes**: This is the default landing page. KPI cards use conditional formatting (green/amber/red) based on targets defined in `kpi-definition.md`.

### Ticket Trends

- **Purpose**: Detailed volume analysis to identify patterns, spikes, and seasonal trends.
- **Audience**: Analysts, operations managers
- **Key Visuals**:
  - Stacked bar chart: Monthly ticket volume by category
  - Line chart: Weekly ticket creation trend
  - Matrix: Tickets by category and channel
- **Filters / Slicers**: Date range, Category, Channel, Priority
- **Drillthrough**: No
- **Notes**: Includes a toggle bookmark to switch between monthly and weekly views.

### SLA Performance

- **Purpose**: Tracks SLA compliance rates and identifies where targets are being missed.
- **Audience**: Operations managers, team leads
- **Key Visuals**:
  - Gauge: Overall SLA Compliance % vs 90% target
  - Clustered bar chart: SLA Compliance % by priority level
  - Heat map: SLA Compliance % by category and month
  - Table: Tickets breaching SLA with resolution hours
- **Filters / Slicers**: Date range, Priority, Category, Assignee Team
- **Drillthrough**: No
- **Notes**: The SLA breach table at the bottom shows individual tickets that exceeded their SLA target, sorted by overage.

### Assignee Scorecard

- **Purpose**: Performance tracking at the individual assignee and team level.
- **Audience**: Team leads
- **Key Visuals**:
  - Table: Assignee name, Closed Tickets, Avg Resolution Hours, SLA Compliance %, CSAT Score
  - Bar chart: Closed tickets by assignee (top 10)
  - KPI cards: Team-level aggregates
- **Filters / Slicers**: Date range, Team, Assignee
- **Drillthrough**: No
- **Notes**: Active assignees only (`IsActive = TRUE`). Historical performance for departed assignees is still visible via the Assignee slicer.

### Backlog Analysis

- **Purpose**: Analysis of currently open tickets to identify aging, bottlenecks, and priority distribution.
- **Audience**: Operations managers, analysts
- **Key Visuals**:
  - Table: Open tickets with TicketID, OpenDate, Category, Priority, Assignee, Age in Days
  - Bar chart: Backlog by category
  - Treemap: Backlog by priority and category
- **Filters / Slicers**: Category, Priority, Assignee
- **Drillthrough**: No
- **Notes**: The date slicer is intentionally disabled on this page. Backlog always shows the current state (`Backlog Count` uses `ALL(DimDate)`).

## Navigation Structure

```text
Executive Summary (landing page)
|-- Ticket Trends
|-- SLA Performance
|-- Assignee Scorecard
`-- Backlog Analysis
```

Navigation uses page navigation buttons at the top of each page. No hierarchical drillthrough - all pages are accessible from any other page.

## Notes

- No hidden pages, tooltip pages, or drillthrough pages in the current version.
- A tooltip page for individual ticket detail is planned for a future release.
