# .claude Folder

This folder contains Claude Code configuration for the Power BI Model Docs Framework.

## Skills

Six skills in `skills/`:

| Skill | Purpose |
|-------|---------|
| create-model-docs | Scaffold a full documentation set from templates |
| review-documentation | Review docs against framework standards |
| generate-measure-catalog-entry | Create a measure catalog entry from DAX |
| update-release-notes | Append a formatted release entry |
| validate-completeness | Check for missing or incomplete templates |
| create-template-from-pattern | Turn a recurring pattern into a new template |

## Context

The root CLAUDE.md has the full project context. This file provides local context for the skills folder only.

Skills should:
- Reference templates from `templates/` by their exact file names
- Follow the writing style and naming conventions from the root CLAUDE.md
- Produce output consistent with the example in `examples/support-operations-analytics/`
