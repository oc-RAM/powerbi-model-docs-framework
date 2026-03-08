---
name: generate-measure-catalog-entry
description: "Use this skill when the user wants to document a single DAX measure or add an entry to the measure catalog. Triggers when the user provides a DAX expression and wants it documented, says things like 'document this measure', 'add this to the measure catalog', 'create a measure entry', or 'generate measure documentation from this DAX'. Produces a formatted measure catalog entry."
tools: Read, Write, Edit, Grep
---

# Generate Measure Catalog Entry

Creates a formatted measure catalog entry from a DAX expression, following the measure-catalog.md template structure.

## Prerequisites

- The user provides a DAX measure expression (at minimum: measure name and DAX formula)
- Optionally: display folder, format string, business context

## Workflow

1. **Parse the DAX expression** to extract:
   - Measure name
   - DAX formula
   - Referenced tables and columns
   - Referenced measures (dependencies)

2. **Generate the catalog entry** with these fields:
   - **Measure Name**: Extracted from the DAX
   - **DAX Expression**: The full formula in backticks
   - **Format**: Inferred from the DAX (count -> `#,0`, percentage -> `0.0%`, average -> `#,0.0`) or as provided
   - **Description**: A plain-language explanation of what the measure calculates
   - **Dependencies**: Other measures referenced in the DAX
   - **Business Context**: Why this measure exists (ask the user if not obvious)

3. **Format the entry** in two forms:

   **Table row format** (for adding to the measures table):
   ```
   | Measure Name | `DAX expression` | Format | Description | Dependencies | Business context |
   ```

   **Detailed format** (for complex measures):
   ```markdown
   ### [Measure Name]

   - **Display Folder**:
   - **Format String**:
   - **Description**:
   - **DAX**:
     ```dax
     [Full DAX expression]
     ```
   - **Dependencies**:
   - **Business Context**:
   - **Notes**:
   ```

4. **If the user specifies a target file**, append the entry to the existing measure-catalog.md in the appropriate section.

5. **If no target file is specified**, present the entry for the user to copy.

## Output

A formatted measure catalog entry ready to add to a measure-catalog.md file.

## Rules

- Follow the measure-catalog.md template format exactly
- Write descriptions in plain language, not DAX jargon
- Always identify dependencies (other measures referenced)
- Infer format strings from DAX patterns but confirm with the user if ambiguous
- If business context is not provided and cannot be inferred, ask the user
- Use the naming conventions from the root CLAUDE.md
