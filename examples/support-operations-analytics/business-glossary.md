# Business Glossary

## Summary

| Field | Value |
|-------|-------|
| Project / Domain | Support Operations Analytics |
| Last Updated | 2025-03-08 |
| Total Terms Defined | 14 |

## Terms

| Term | Definition | Source of Truth | Related Measures | Owner | Last Reviewed |
|------|-----------|-----------------|-----------------|-------|--------------|
| Ticket | A single recorded request for support or service. Each ticket has a unique ID, a creation date, and a resolution status. | Ticketing system | Total Tickets, Open Tickets, Closed Tickets | Operations Manager | 2025-03-08 |
| Open Ticket | A ticket that has not yet been resolved. CloseDate is null and IsResolved is FALSE. | Model definition | Open Tickets, Backlog Count | Operations Manager | 2025-03-08 |
| Closed Ticket | A ticket that has been resolved and has a non-null CloseDate. Includes tickets regardless of whether they met SLA. | Model definition | Closed Tickets | Operations Manager | 2025-03-08 |
| Resolution Time | The elapsed hours between a ticket's OpenDate and CloseDate. Measured in decimal hours (e.g., 6.5 hours). Does not exclude weekends or non-business hours. | Model calculation | Avg Resolution Hours, Median Resolution Hours | Operations Manager | 2025-03-08 |
| SLA Target | The maximum allowed resolution time (in hours) for a ticket, determined by its priority level at creation. Set in the SLA agreement, not changeable per ticket. | Service Level Agreement v3.1 | SLA Compliance % | Service Quality Lead | 2025-03-08 |
| SLA Compliance | A ticket is "SLA compliant" if its actual resolution time is less than or equal to its SLA target. The SLA Compliance % is the ratio of compliant tickets to all closed tickets. | Service Level Agreement v3.1 | SLA Compliance %, SLA Met Count | Operations Manager | 2025-03-08 |
| Backlog | The set of all currently open tickets, regardless of when they were created. Measured as a count (Backlog Count). Not filtered by date slicer. | Internal definition | Backlog Count | Team Lead | 2025-03-08 |
| CSAT | Customer Satisfaction score. A rating from 1 (very dissatisfied) to 5 (very satisfied) provided by the requester after ticket resolution via an optional survey. | Customer experience policy | CSAT Score, CSAT Response Rate | Service Quality Lead | 2025-03-08 |
| First Contact Resolution | A ticket resolved within 1 hour of creation. Used as a proxy for issues that were handled immediately without escalation or follow-up. | Internal definition (proxy) | First Contact Resolution % | Operations Manager | 2025-03-08 |
| Assignee | The support team member responsible for resolving a ticket. Refers to the current assignee, not the full assignment history. | HR System Extract | Assignee Utilization | Team Lead | 2025-03-08 |
| Requester | The person or department that submitted the ticket. Identified by name and department. | Customer Directory | - | Customer Ops | 2025-03-08 |
| Category | The classification of a ticket by subject area (e.g., Hardware, Software, Network, Access). Assigned at ticket creation. | Ticketing system | - | Operations Manager | 2025-03-08 |
| Priority | The urgency level of a ticket. One of: Critical, High, Medium, Low. Determines the SLA target. | Ticketing system + SLA | - | Operations Manager | 2025-03-08 |
| Channel | How the ticket was submitted: Email, Phone, Portal, Chat, or Walk-in. | Ticketing system | - | Operations Manager | 2025-03-08 |

## Acronyms

| Acronym | Full Form | Context |
|---------|-----------|---------|
| SLA | Service Level Agreement | The contract defining resolution time targets by priority |
| CSAT | Customer Satisfaction | Post-resolution survey score |
| KPI | Key Performance Indicator | Measured metrics with defined targets |
| FCR | First Contact Resolution | Tickets resolved within 1 hour |

## Definition Disputes

| Term | Dispute | Resolution | Date | Decided By |
|------|---------|-----------|------|-----------|
| Resolution Time | Should weekends and non-business hours be excluded from the calculation | No - resolution time uses calendar hours, not business hours. This simplifies the calculation and aligns with the SLA agreement, which defines targets in calendar hours. | 2024-04-10 | Operations Manager |
| First Contact Resolution | Should the threshold be 30 minutes instead of 1 hour | 1 hour was kept as the threshold because the data does not have granularity below 1-hour increments in the source system. | 2024-06-20 | Operations Manager |

## Notes

- Terms in this glossary are specific to this model and its reports. They may differ from how the same words are used in other contexts within the organization.
- When adding measures that introduce new business concepts, add the corresponding term here first, then reference it in the measure catalog.
