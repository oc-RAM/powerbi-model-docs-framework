# Example: Support Operations Analytics

This folder contains a complete worked example of the Power BI Model Docs Framework applied to a generic support operations analytics model.

## About This Example

The **Support Operations Analytics** model is a fictional semantic model for a service desk / help desk operation. It tracks tickets, resolution performance, SLA compliance, customer satisfaction, and assignee workload.

This example is intentionally generic. It does not reference any specific company, product, or platform. You can use it as a reference when documenting your own models.

All names, paths, teams, environments, and roles in this example are fictional. They are included only to demonstrate reusable documentation patterns.

## What Is Documented

Every template from the framework is filled in with realistic content:

| Document | Description |
|----------|-------------|
| [model-overview.md](model-overview.md) | High-level summary of the model |
| [source-inventory.md](source-inventory.md) | Data sources feeding the model |
| [table-inventory.md](table-inventory.md) | All tables with type, grain, and row counts |
| [column-dictionary.md](column-dictionary.md) | Column definitions for key tables |
| [measure-catalog.md](measure-catalog.md) | All measures with DAX and descriptions |
| [relationship-map.md](relationship-map.md) | Table relationships and cardinality |
| [power-query-docs.md](power-query-docs.md) | Power Query transformation logic |
| [report-page-inventory.md](report-page-inventory.md) | Report pages and their purpose |
| [kpi-definition.md](kpi-definition.md) | KPI definitions with targets and thresholds |
| [business-glossary.md](business-glossary.md) | Shared business terms and definitions |
| [refresh-deployment-notes.md](refresh-deployment-notes.md) | Refresh schedule and deployment process |
| [handover-summary.md](handover-summary.md) | Handover context for transitions |
| [issue-decision-log.md](issue-decision-log.md) | Design decisions and open issues |
| [release-notes.md](release-notes.md) | Version history |

## Model Summary

| Aspect | Details |
|--------|---------|
| Fact Table | FactTicket |
| Dimensions | DimAssignee, DimCategory, DimPriority, DimRequester, DimChannel, DimDate |
| Key Measures | Total Tickets, SLA Compliance %, Avg Resolution Hours, CSAT Score |
| Report Pages | 5 (Executive Summary, Ticket Trends, SLA Performance, Assignee Scorecard, Backlog Analysis) |

## How to Use This Example

1. Browse the files to see what good documentation looks like for each template.
2. Compare them with the blank templates in [templates/](../../templates/).
3. Use the example as a reference when filling in your own templates.
4. See [guides/using-the-examples.md](../../guides/using-the-examples.md) for more detail.
