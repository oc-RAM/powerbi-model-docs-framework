---
name: review-documentation
description: "Use this skill when the user wants to review, audit, or check the quality of existing Power BI model documentation against the framework standards. Triggers when the user says things like 'review my docs', 'audit documentation', 'check documentation quality', 'are my docs complete', 'review against the framework', or 'find documentation gaps'. Reads existing documentation files and reports issues."
tools: Read, Glob, Grep
---

# Review Documentation

Reviews an existing set of model documentation files against the Power BI Model Docs Framework standards and reports gaps, inconsistencies, and quality issues.

## Prerequisites

- The user must provide the path to a folder containing documentation files
- The folder should contain files following the framework template naming conventions

## Workflow

1. **Scan the target folder** for documentation files using Glob.

2. **Check file presence** against the 14 expected templates:
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

3. **For each present file**, read it and check:
   - Is the Summary table filled in (Model Name, Last Updated)
   - Are the main content tables populated (not just headers)
   - Are blockquote instructions still present (suggesting the file has not been customized)
   - Are there placeholder values like "TBD", empty table rows, or blank fields
   - Does the content follow the framework naming conventions

4. **Cross-reference checks**:
   - Do measure names in measure-catalog.md match those referenced in kpi-definition.md
   - Do table names in table-inventory.md match those in relationship-map.md
   - Do business glossary terms align with measure descriptions
   - Are Last Updated dates recent or stale (> 90 days)

5. **Generate a report** with:
   - **Missing files**: Templates not present in the folder
   - **Incomplete files**: Files with unfilled sections or placeholder content
   - **Stale files**: Files with Last Updated dates older than 90 days
   - **Inconsistencies**: Cross-reference mismatches between files
   - **Suggestions**: Specific improvements ranked by importance

## Output Format

```markdown
## Documentation Review: [Model Name]

### Summary
- Files present: X / 14
- Files complete: X / Y
- Stale files: X
- Issues found: X

### Missing Files
- [list]

### Incomplete Files
- [file]: [specific issues]

### Inconsistencies
- [description]

### Suggestions
1. [highest priority suggestion]
2. [next suggestion]
```

## Rules

- Do not modify any files - this is a read-only review
- Be specific about what is missing or incomplete
- Prioritize suggestions by impact (measure catalog completeness > formatting issues)
- Reference the example project in `examples/support-operations-analytics/` as the quality benchmark
