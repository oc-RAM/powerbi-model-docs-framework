# Adapting the Framework

This framework provides a generic structure that works across different Power BI projects. Most teams will need to adapt it to fit their specific needs. This guide explains how.

## When to Adapt

Adapt the framework when:

- Your project has documentation needs not covered by the existing templates
- Your organization has naming conventions or standards that differ from the framework defaults
- You need fewer templates (simpler model) or more templates (complex enterprise model)
- You work in a regulated industry with additional documentation requirements

## What to Adapt

### Template Selection

Not every model needs all 14 templates. Choose based on your project's complexity:

| Model Complexity | Recommended Templates |
|-----------------|----------------------|
| Simple (< 5 tables, < 10 measures) | model-overview, table-inventory, measure-catalog, release-notes |
| Medium (5-15 tables, 10-50 measures) | Add: relationship-map, column-dictionary, source-inventory, kpi-definition |
| Complex (15+ tables, 50+ measures) | All templates |
| Governed / Regulated | All templates + business-glossary + handover-summary |

### Template Sections

Each template includes optional sections marked with `<!-- Optional -->`. Remove these if they do not apply. You can also add sections specific to your project.

**Adding a section:**

1. Add a new `##` heading in the relevant template.
2. Include a brief description of what the section covers.
3. Provide a table or list structure for the content.
4. Update the example file to show the section in use if that would help.

### Naming Conventions

The framework uses these defaults:

| Element | Default Convention |
|---------|-------------------|
| File names | kebab-case (`measure-catalog.md`) |
| Section headers | Title Case (`## Data Sources`) |
| Table column headers | Title Case |

If your team uses different conventions, apply them consistently. The structure matters more than the exact naming.

### Folder Structure

The default structure places all documentation files in a flat folder. For projects with multiple models or reports, consider:

```text
project-docs/
|-- shared/
|   |-- business-glossary.md
|   `-- kpi-definition.md
|-- model-a/
|   |-- model-overview.md
|   |-- table-inventory.md
|   `-- measure-catalog.md
`-- model-b/
    |-- model-overview.md
    |-- table-inventory.md
    `-- measure-catalog.md
```

Shared files such as the business glossary can live in a parent folder to avoid duplication.

## What Not to Adapt

Some things should stay consistent even when adapting:

- **Release notes format.** Keep reverse chronological order and consistent entry structure.
- **Measure catalog fields.** Always include the DAX expression, description, and business context.
- **Relationship map columns.** Cardinality and cross-filter direction are always relevant.
- **Template structure.** Keep the Summary table at the top of each file for scanability.

## Industry-Specific Adaptations

### Regulated Industries (Finance, Healthcare)

- Add an "Audit Trail" section to templates that tracks who changed what and when.
- Add a "Data Classification" column to the column dictionary (Public, Internal, Confidential, Restricted).
- Add a "Regulatory Requirement" field to KPI definitions.

### Consulting / Client Delivery

- Add a "Client Sign-off" section to the handover summary.
- Include a "Scope of Work Reference" in the model overview.
- Keep a separate issue-decision-log per engagement phase.

### Enterprise / Multi-model Environments

- Use a shared business glossary across models.
- Create a model index file listing all documented models.
- Add cross-model dependency documentation.

## Creating New Templates

If you need a template that does not exist in the framework:

1. Check the [ROADMAP.md](../ROADMAP.md) - it may already be planned.
2. Follow the existing template structure: Summary table at the top, main content in tables, optional sections marked, usage notes in blockquotes.
3. Create a filled-in example in the examples folder.
4. Consider contributing it back to the framework (see [CONTRIBUTING.md](../CONTRIBUTING.md)).

If you use Claude Code, the `create-template-from-pattern` skill can help you build a new template that follows the framework's conventions.
