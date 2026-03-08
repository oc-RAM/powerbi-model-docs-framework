# Claude Code Integration

This framework includes optional Claude Code support through a project-level CLAUDE.md and a set of reusable skills. This integration is not required - the framework works with any editor. Claude Code enhances the workflow for teams that use it.

## What Is Included

| Component | Location | Purpose |
|-----------|----------|---------|
| Project CLAUDE.md | `CLAUDE.md` (root) | Gives Claude Code context about the repo's structure, style, and rules |
| Skills folder | `.claude/skills/` | Reusable workflows for common documentation tasks |

### Available Skills

| Skill | Purpose |
|-------|---------|
| `create-model-docs` | Scaffolds a full documentation set from templates for a new model |
| `review-documentation` | Reviews existing docs against framework standards and flags gaps |
| `generate-measure-catalog-entry` | Creates a measure catalog entry from a DAX expression |
| `update-release-notes` | Appends a new release entry with consistent formatting |
| `validate-completeness` | Checks a documentation folder for missing or incomplete templates |
| `create-template-from-pattern` | Helps maintainers turn a recurring doc pattern into a new template |

## Setup

### If You Already Use Claude Code

1. Clone or download this repository
2. Open it in your terminal / editor
3. Claude Code will automatically read the root `CLAUDE.md` for project context
4. Skills in `.claude/skills/` are available for use

### If You Are New to Claude Code

1. Install Claude Code from [claude.ai/claude-code](https://claude.ai/claude-code)
2. Clone this repository
3. Navigate to the repository folder
4. Run `claude` to start a session

Claude Code will use the CLAUDE.md file to understand the project and follow its conventions.

## Using the Skills

### Scaffold Documentation for a New Model

Tell Claude Code to create documentation for a new model:

```
Create documentation for my "Sales Analytics" model using the framework templates
```

The `create-model-docs` skill will:
1. Copy all 14 templates into a new folder
2. Pre-fill headers and summary fields based on your input
3. Set up the file structure

### Generate a Measure Catalog Entry

Provide a DAX expression and ask Claude Code to document it:

```
Document this measure: Revenue YTD = TOTALYTD(SUM(FactSales[Amount]), DimDate[Date])
```

The `generate-measure-catalog-entry` skill will create a formatted entry with the expression, description, format, dependencies, and business context.

### Review Documentation Quality

Ask Claude Code to review your documentation:

```
Review the documentation in my-project/ against the framework standards
```

The `review-documentation` skill will check for:
- Missing templates
- Incomplete sections
- Inconsistent formatting
- Missing business context in measures

### Add a Release Notes Entry

After making changes:

```
Add a release note: Added three new measures for customer segmentation
```

The `update-release-notes` skill will append a formatted entry with the correct structure.

### Check Completeness

```
Validate the completeness of documentation in my-project/
```

The `validate-completeness` skill will report which templates are present, which are missing, and which have unfilled sections.

## How CLAUDE.md Helps

The root CLAUDE.md provides Claude Code with:

- **Repo context**: What this project is and how it is organized
- **Writing style**: Practical, direct, structured - no jargon or hype
- **Naming conventions**: kebab-case files, Title Case headers
- **Public-safety rules**: Never include proprietary content, client names, or confidential data
- **Template rules**: How templates should be structured and extended
- **Consistency rules**: How to maintain uniformity across files

This means Claude Code will follow the framework's conventions automatically when creating or editing documentation files.

## Without Claude Code

If you do not use Claude Code, the framework is fully functional:

- Templates are plain markdown files you fill in manually
- Guides explain the workflow step by step
- The example project shows what good documentation looks like
- No Claude Code dependency is required for any part of the framework

Claude Code support is an enhancement for teams that want to speed up documentation workflows.
