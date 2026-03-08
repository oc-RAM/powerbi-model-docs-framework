---
name: create-template-from-pattern
description: "Use this skill when a maintainer wants to create a new reusable template for the framework based on a recurring documentation pattern. Triggers when the user says things like 'create a new template', 'add a template to the framework', 'turn this pattern into a template', 'I keep documenting X the same way', or 'we need a template for X'. Helps maintainers build new templates that follow existing framework conventions."
tools: Read, Write, Edit, Glob, Grep
---

# Create Template From Pattern

Helps framework maintainers turn a recurring documentation pattern into a new reusable template that follows the framework's existing structure, naming, and style conventions.

## Prerequisites

- The user describes the documentation need or provides an example of the pattern they want to standardize
- The user should explain who would use this template and what problem it solves

## Workflow

1. **Understand the pattern**:
   - What documentation need does this serve
   - Who is the audience
   - Is this need common enough to justify a reusable template (> 10% of projects)
   - Is it already covered by an existing template

2. **Check for overlap** with existing templates:
   - Read `templates/README.md` to see the current template index
   - Scan existing templates to verify the need is not already addressed
   - If overlap exists, suggest adding a section to the existing template instead

3. **Design the template** following framework conventions:

   **Structure** (must follow this pattern):
   ```markdown
   # [Template Title]

   > Remove these blockquote instructions when filling in this template.

   ## Summary

   | Field | Value |
   |-------|-------|
   | Model Name | |
   | Last Updated | |
   | [domain-specific field] | |

   ## [Main Content Section]

   [Tables, lists, or structured content]

   <!-- Optional -->
   ## [Optional Section]

   [Content]

   ## Notes

   -
   ```

   **Naming**: kebab-case file name (e.g., `rls-documentation.md`)
   **Headers**: Title Case
   **Content**: Markdown tables for structured data, blockquote instructions for guidance

4. **Create the template file** in `templates/`

5. **Create a corresponding example file** in `examples/support-operations-analytics/` with realistic content that fits the Support Operations Analytics model

6. **Update supporting files**:
   - Add the template to the index table in `templates/README.md`
   - Consider whether it should be in the "Recommended Starting Set"
   - Note that `CHANGELOG.md` should be updated (inform the user)

7. **Update affected skills** (inform the user):
   - `validate-completeness` may need the new template in its checklist
   - `create-model-docs` should include the new template in its scaffold list

## Output

- New template file in `templates/`
- New example file in `examples/support-operations-analytics/`
- Updated `templates/README.md`
- List of other files that should be updated

## Rules

- Follow the exact template structure pattern used by all other templates
- Include blockquote usage instructions in the template
- Include a Summary table at the top
- Mark truly optional sections with `<!-- Optional -->`
- End with a `## Notes` section
- The example must use the same model entities as the existing example (FactTicket, DimAssignee, etc.)
- Do not add templates for edge cases - the documentation need must be broadly applicable
- Refer the user to `guides/maintaining-the-framework.md` for the full checklist
