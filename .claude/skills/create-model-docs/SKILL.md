---
name: create-model-docs
description: "Use this skill when the user wants to create, scaffold, or set up documentation for a new Power BI semantic model using the framework templates. Triggers when the user says things like 'create docs for my model', 'scaffold documentation', 'set up model docs', 'document a new model', or 'initialize documentation folder'. Creates all 14 template files pre-filled with model-specific header information."
tools: Read, Write, Glob, Grep
---

# Create Model Documentation

Scaffolds a complete documentation set for a new Power BI semantic model by copying and pre-filling all 14 framework templates.

## Prerequisites

- The user must provide a model name
- The user should provide a target folder path (or you choose a sensible default)
- Optionally, the user provides: description, owner, refresh frequency, table count, measure count

## Workflow

1. **Gather basic information** from the user:
   - Model name (required)
   - Target folder path (required)
   - Description, owner, refresh frequency (optional - can be filled in later)

2. **Read each template** from the `templates/` folder:
   - model-overview.md
   - source-inventory.md
   - table-inventory.md
   - column-dictionary.md
   - measure-catalog.md
   - relationship-map.md
   - power-query-docs.md
   - report-page-inventory.md
   - kpi-definition.md
   - business-glossary.md
   - refresh-deployment-notes.md
   - handover-summary.md
   - issue-decision-log.md
   - release-notes.md

3. **For each template**, create a copy in the target folder with:
   - Model Name filled in the Summary table
   - Last Updated set to today's date
   - Other provided fields filled in where applicable
   - Blockquote instructions preserved (the user will remove them as they fill in content)

4. **Create a README.md** in the target folder listing all documentation files with links.

5. **Create an initial release-notes entry**:
   ```markdown
   ### v1.0 - Initial Documentation

   **Released**: [today's date]
   **Released By**: [owner if provided, otherwise leave blank]

   **Changes**:

   - Initial documentation scaffold created using the Power BI Model Docs Framework
   ```

6. **Report** to the user which files were created.

## Output

- 14 template files + 1 README.md in the target folder
- Each file pre-filled with available model information
- Release notes initialized with a first entry

## Rules

- Follow the exact template structure from `templates/`
- Use the writing style from the root CLAUDE.md (practical, direct, no hype)
- Use kebab-case for file names
- Do not invent content the user did not provide - leave fields blank for the user to fill in
- Do not remove optional sections - the user decides what to keep
