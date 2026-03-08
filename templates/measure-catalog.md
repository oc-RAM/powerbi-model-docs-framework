# Measure Catalog

> Remove these blockquote instructions when filling in this template.

## Summary

| Field | Value |
|-------|-------|
| Model Name | |
| Last Updated | |
| Total Measures | |

> Document all measures in the semantic model. Group by display folder or business area for readability.

## Measures

### [Display Folder / Business Area]

| Measure Name | DAX Expression | Format | Description | Dependencies | Business Context |
|-------------|----------------|--------|-------------|--------------|------------------|
| | `[DAX here]` | Number / % / Currency / Date | | | |
| | | | | | |

> **DAX Expression**: The full DAX formula. Use backticks for inline code or a code block for longer expressions.
>
> **Format**: The display format string or category (e.g., `#,0`, `0.0%`, `$#,0.00`).
>
> **Description**: What this measure calculates, in plain language.
>
> **Dependencies**: Other measures or calculated columns this measure references.
>
> **Business Context**: Why this measure exists - what business question it answers or what decision it supports.

## Detailed Measure Documentation

> For complex measures, add a detailed entry below. This is useful for measures with conditional logic, time intelligence, or multiple dependencies.

### [Measure Name]

- **Display Folder**:
- **Format String**:
- **Description**:
- **DAX**:
  ```dax
  [Full DAX expression here]
  ```
- **Dependencies**:
- **Business Context**:
- **Notes**:

## Measure Naming Conventions

<!-- Optional -->

> If this model follows specific measure naming patterns, document them here.

| Pattern | Convention | Example |
|---------|-----------|---------|
| Counts | No prefix | `Total Tickets`, `Open Tickets` |
| Ratios / Rates | Suffix with `%` or `Rate` | `SLA Compliance %`, `Resolution Rate` |
| Averages | Prefix with `Avg` | `Avg Resolution Hours` |
| Time Intelligence | Suffix with period | `Total Tickets MTD`, `Revenue YoY` |
| Targets | Suffix with `Target` | `SLA Target`, `CSAT Target` |

## Notes

-
