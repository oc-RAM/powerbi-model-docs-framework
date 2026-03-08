---
name: validate-completeness
description: "Use this skill when the user wants to check whether a documentation folder is complete, has all required templates, and has no unfilled sections. Triggers when the user says things like 'validate my docs', 'check completeness', 'is my documentation complete', 'what am I missing', 'audit documentation completeness', or 'check for gaps'. Performs a structural completeness check."
tools: Read, Glob, Grep
---

# Validate Completeness

Checks a documentation folder for missing templates, unfilled sections, and structural issues against the framework's expected standard.

## Prerequisites

- The user provides the path to a documentation folder

## Workflow

1. **Scan the folder** for all markdown files.

2. **Check against the expected template list**:

   **Essential templates** (should be present for any documented model):
   - model-overview.md
   - table-inventory.md
   - measure-catalog.md
   - relationship-map.md
   - release-notes.md

   **Recommended templates** (should be present for well-documented models):
   - source-inventory.md
   - column-dictionary.md
   - kpi-definition.md
   - business-glossary.md
   - report-page-inventory.md

   **Situational templates** (present when applicable):
   - power-query-docs.md
   - refresh-deployment-notes.md
   - handover-summary.md
   - issue-decision-log.md

3. **For each present file**, check:
   - **Summary table**: Is the Model Name filled in Is Last Updated present and not a placeholder
   - **Main content**: Are the primary tables populated with at least one data row
   - **Blockquote instructions**: Are template instructions still present (suggesting the file was copied but not filled in)
   - **Placeholder content**: Are there "TBD", "[fill in]", or empty cells in required fields

4. **Score each file**:
   - **Complete**: Summary filled, main content populated, no placeholders
   - **Partial**: Some sections filled, others empty or placeholder
   - **Scaffold only**: File exists but has not been customized beyond the template

5. **Generate the report**:

   ```markdown
   ## Completeness Report: [folder name]

   ### File Presence
   - Essential: X / 5 present
   - Recommended: X / 5 present
   - Situational: X / 4 present
   - Total: X / 14

   ### File Quality
   | File | Status | Issues |
   |------|--------|--------|
   | model-overview.md | Complete / Partial / Scaffold / Missing | [specific issues] |
   | ... | ... | ... |

   ### Priority Actions
   1. [Most important action]
   2. [Next action]
   3. [Next action]
   ```

## Output

A completeness report showing what is present, what is missing, and what needs attention, with prioritized action items.

## Rules

- Do not modify any files - this is a read-only check
- Distinguish between "missing" (file not present) and "incomplete" (file present but not filled in)
- Prioritize actions by impact: measure catalog > table inventory > column dictionary
- Do not flag situational templates as missing unless the user's model clearly needs them
- Reference the example project as the quality benchmark
