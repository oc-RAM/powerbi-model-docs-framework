# Refresh and Deployment Notes

## Summary

| Field | Value |
|-------|-------|
| Model Name | Support Operations Analytics |
| Last Updated | 2025-03-08 |
| Workspace | Example Production Workspace |
| Gateway | On-premises Data Gateway (ExampleGateway) |
| Refresh Type | Scheduled (Full Extract) |

## Refresh Schedule

| Schedule | Time (UTC) | Days | Timeout | Notes |
|----------|-----------|------|---------|-------|
| Primary | 06:00 | Mon-Fri | 60 min | Runs after overnight ETL completion |
| Weekend | 08:00 | Sat-Sun | 60 min | Later start, lower priority |

## Refresh Dependencies

| Dependency | Type | Expected Completion | Notes |
|-----------|------|---------------------|-------|
| Overnight ETL pipeline | ETL Pipeline | 05:30 UTC | Loads ticketing database; must complete before refresh |
| HR extract upload | Manual Upload | 1st of each month | `DimAssignee` data may be stale up to 30 days |

## Data Gateway

| Field | Value |
|-------|-------|
| Gateway Name | ExampleGateway |
| Gateway Type | On-premises |
| Managed By | Platform support team |
| Data Sources Configured | Ticketing Database (SQL), repository-based sources (OAuth) |

## Deployment Process

| Step | Action | Responsibility |
|------|--------|---------------|
| 1 | Develop changes in Power BI Desktop | Developer |
| 2 | Publish to development workspace | Developer |
| 3 | Test refresh and report functionality | Developer + Analyst |
| 4 | Request review from reporting owner | Developer |
| 5 | Promote to production via deployment pipeline | Workspace Admin |
| 6 | Verify production refresh succeeds | Developer |
| 7 | Update release notes | Developer |

## Deployment Pipeline

| Stage | Workspace | Purpose |
|-------|-----------|---------|
| Development | Example Development Workspace | Active development and testing |
| Production | Example Production Workspace | Live reporting for stakeholders |

A UAT / staging workspace is not currently used. If the model grows in complexity, a three-stage pipeline is recommended.

## Known Refresh Issues

| Date | Issue | Cause | Resolution |
|------|-------|-------|------------|
| 2024-11-12 | Refresh failed at 06:00 | ETL pipeline delayed due to database maintenance | Manually triggered refresh at 09:00 after ETL completed |
| 2024-08-03 | Refresh timeout | Row count spike from bulk ticket import | Increased timeout from 30 to 60 minutes |

## Contacts

| Role | Name | Responsibility |
|------|------|---------------|
| Data Gateway Admin | Platform support team | Gateway availability and configuration |
| Workspace Admin | BI team lead | Workspace permissions and deployment pipeline |
| Refresh Owner | Reporting analyst | Monitoring daily refresh success |

## Notes

- Incremental refresh is not configured but is feasible using `FactTicket[OpenDate]`. Planned for evaluation when row count exceeds 1M.
- Repository-based data sources authenticate via OAuth. Tokens may expire and require re-authentication by the workspace admin.
