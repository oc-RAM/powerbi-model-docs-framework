# Refresh and Deployment Notes

> Remove these blockquote instructions when filling in this template.

## Summary

| Field | Value |
|-------|-------|
| Model Name | |
| Last Updated | |
| Workspace | |
| Gateway | |
| Refresh Type | Scheduled / On-Demand / Incremental |

## Refresh Schedule

| Schedule | Time (UTC) | Days | Timeout | Notes |
|----------|-----------|------|---------|-------|
| Primary | | | | |
| Secondary | | | | |

> If refreshes are triggered by a pipeline (e.g., Azure Data Factory, Power Automate, or Fabric pipeline), note that here instead of a fixed schedule.

## Refresh Dependencies

> List any upstream processes that must complete before this model refreshes.

| Dependency | Type | Expected Completion | Notes |
|-----------|------|---------------------|-------|
| | ETL Pipeline / Dataflow / Other Model / Manual Upload | | |

## Data Gateway

<!-- Optional - only if an on-premises or VNet gateway is used -->

| Field | Value |
|-------|-------|
| Gateway Name | |
| Gateway Type | On-premises / VNet |
| Managed By | |
| Data Sources Configured | |

## Incremental Refresh

<!-- Optional - only if incremental refresh is configured -->

| Field | Value |
|-------|-------|
| Table | |
| Range (Store) | |
| Range (Refresh) | |
| Date Column | |
| Detect Data Changes | Yes / No |

## Deployment Process

> Describe how changes to this model are published.

| Step | Action | Responsibility |
|------|--------|---------------|
| 1 | | |
| 2 | | |
| 3 | | |

> Example flow: develop in Desktop -> publish to Dev workspace -> test -> promote to Production via deployment pipeline.

## Deployment Pipeline

<!-- Optional -->

| Stage | Workspace | Purpose |
|-------|-----------|---------|
| Development | | Active development and testing |
| Test / UAT | | Stakeholder validation |
| Production | | Live reporting |

## Known Refresh Issues

> Document any recurring or past refresh failures and their resolutions.

| Date | Issue | Cause | Resolution |
|------|-------|-------|------------|
| | | | |

## Contacts

| Role | Name | Responsibility |
|------|------|---------------|
| Data Gateway Admin | | |
| Workspace Admin | | |
| Refresh Owner | | |

## Notes

-
