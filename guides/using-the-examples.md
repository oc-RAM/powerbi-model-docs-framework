# Using the Examples

The `examples/support-operations-analytics/` folder contains a complete worked example of the framework applied to a fictional support operations model. This guide explains how to use it effectively.

## What the Example Shows

The example documents a generic support ticket tracking model with:

- 1 fact table (FactTicket) and 6 dimension tables
- 12 measures covering volume, SLA, satisfaction, backlog, and productivity
- 5 report pages
- 5 KPIs with targets and thresholds
- A business glossary with 14 terms
- A complete decision log and release history

Every template from the `templates/` folder is filled in with realistic content.

## How to Use the Example

### As a Reference

When filling in a template for your own model, open the corresponding example file side-by-side. It shows:

- What level of detail to aim for
- How to phrase descriptions
- How to fill in table fields
- What "good" documentation looks like

### As a Starting Point

If your model is similar to the example (ticket-based, operational, service-oriented), you can:

1. Copy the example folder
2. Rename it to match your model
3. Replace the content with your own data
4. Delete sections that do not apply

This is faster than starting from blank templates.

### As a Quality Benchmark

After documenting your own model, compare your files to the example:

- Is your model overview as clear
- Does your measure catalog include business context
- Does your business glossary address potential term confusion
- Do your release notes capture meaningful changes

## What the Example Is Not

- It is not a real model. The data, measures, and business rules are fictional.
- It is not the only way to use the templates. Your model may need more or fewer sections.
- It is not exhaustive. A production model may have hundreds of measures - the example has 12 to demonstrate the format without being overwhelming.

## Key Patterns to Notice

### Measure Catalog

The example groups measures by business area (Volume, Resolution Performance, SLA, Customer Satisfaction, Backlog, Productivity). It includes a detailed documentation section for complex measures like SLA Compliance % and Backlog Count.

### Business Glossary

The example includes a "Definition Disputes" section that documents cases where stakeholders disagreed on a term's meaning. This is one of the most valuable sections for governance - it prevents the same debate from recurring.

### Issue and Decision Log

The example separates decisions from issues. Decisions are settled and documented with alternatives considered. Issues are tracked with status and priority. This separation makes the log useful both for understanding past choices and tracking current work.

### Release Notes

The example uses semantic versioning (major.minor.patch) with clear change descriptions and impact notes. Each entry explains what changed **and why**.

## Tips

- The example is intentionally thorough. For a simpler model, your documentation can be shorter.
- Focus on the structure and level of detail, not the specific content.
- If a template section does not apply to your model, delete it rather than leaving it empty.
