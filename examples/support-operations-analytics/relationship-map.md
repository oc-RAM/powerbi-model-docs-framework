# Relationship Map

## Summary

| Field | Value |
|-------|-------|
| Model Name | Support Operations Analytics |
| Last Updated | 2025-03-08 |
| Total Relationships | 6 |
| Active Relationships | 6 |
| Inactive Relationships | 0 |

## Relationships

| # | From Table | From Column | To Table | To Column | Cardinality | Cross-filter Direction | Active | Notes |
|---|-----------|-------------|----------|-----------|-------------|----------------------|--------|-------|
| 1 | FactTicket | OpenDateKey | DimDate | DateKey | Many-to-One | Single | Yes | Primary date relationship |
| 2 | FactTicket | AssigneeKey | DimAssignee | AssigneeKey | Many-to-One | Single | Yes | |
| 3 | FactTicket | CategoryKey | DimCategory | CategoryKey | Many-to-One | Single | Yes | |
| 4 | FactTicket | PriorityKey | DimPriority | PriorityKey | Many-to-One | Single | Yes | |
| 5 | FactTicket | RequesterKey | DimRequester | RequesterKey | Many-to-One | Single | Yes | |
| 6 | FactTicket | ChannelKey | DimChannel | ChannelKey | Many-to-One | Single | Yes | |

## Relationship Diagram

```
DimDate          DimAssignee       DimCategory
  |                  |                 |
  |  (OpenDateKey)   |  (AssigneeKey)  |  (CategoryKey)
  |                  |                 |
  +--------+---------+---------+-------+
           |                   |
         FactTicket          FactTicket
           |                   |
  +--------+---------+---------+-------+
  |                  |                 |
  |  (PriorityKey)   |  (RequesterKey) |  (ChannelKey)
  |                  |                 |
DimPriority      DimRequester       DimChannel
```

This is a classic star schema. All six dimension tables connect directly to the single fact table (FactTicket) through many-to-one relationships with single-direction cross-filtering.

## Notes

- No bidirectional filters are used. This keeps the model simple and avoids ambiguous filter paths.
- No inactive relationships exist. If a future requirement needs to filter FactTicket by CloseDate through DimDate, an inactive relationship would be added and activated via USERELATIONSHIP() in specific measures.
- All relationships use integer key columns for optimal performance.
- The DimDate relationship uses OpenDateKey (not CloseDate) as the active path. This means time-based filters slice tickets by when they were opened, not when they were closed.
