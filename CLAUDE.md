# Power BI Model Docs Framework

A reusable documentation framework for Power BI semantic models. Provides markdown templates, guides, and a worked example for documenting models consistently.

## File Structure

```
templates/       14 reusable markdown templates (the core product)
examples/        Worked example: Support Operations Analytics model
guides/          8 practical guides for usage and maintenance
.claude/skills/  6 Claude Code skills for documentation workflows
```

Root files: README, LICENSE (MIT), CONTRIBUTING, CODE_OF_CONDUCT, CHANGELOG, ROADMAP, PROJECT_SCOPE.

## Writing Style

- Practical, direct, structured
- Low jargon - use standard Power BI terminology only
- Short sentences, clear descriptions
- No hype, no marketing language, no "AI magic" phrasing
- Write for working professionals, not academic audiences
- Business context matters more than technical descriptions

## Naming Conventions

- File names: kebab-case (`measure-catalog.md`, `table-inventory.md`)
- Section headers: Title Case (`## Data Sources`, `## Known Limitations`)
- Template table headers: Title Case
- Skill folders: kebab-case (`create-model-docs/`)
- Example model tables: PascalCase (`FactTicket`, `DimAssignee`, `DimDate`)

## Templates

14 templates in `templates/`. Each follows this structure:
1. Title heading
2. Blockquote usage instructions (removed when filling in)
3. Summary table (Model Name, Last Updated)
4. Main content in markdown tables
5. Optional sections marked with `<!-- Optional -->`
6. Notes section at bottom

When extending or creating templates, follow this structure exactly.

## Public Safety Rules

Never include in any file:
- Real company names, client names, or employer names
- Real project names from production environments
- Proprietary table names, measure names, or KPI definitions from real work
- Screenshots or exports from real systems
- Connection strings, credentials, or access tokens
- Internal governance language copied verbatim from any organization

When in doubt, use a generic example. The example project (Support Operations Analytics) demonstrates the right level of abstraction.

## Contribution Rules

- Keep templates generic - they must work across different organizations
- Keep the example project consistent - all files reference the same model (FactTicket, DimAssignee, etc.)
- Update the example when templates change
- Update skills when template structure changes
- Add a CHANGELOG entry for every meaningful change
- Do not add templates for edge cases affecting fewer than 10% of users
- Do not duplicate content across templates - use links between files

## Consistency

- All templates use the same summary table format at the top
- All example files reference the same model entities (FactTicket, DimAssignee, DimCategory, DimPriority, DimRequester, DimChannel, DimDate)
- Cross-references between files use relative markdown links
- Date format: YYYY-MM-DD
- Measure names in examples match between measure-catalog.md, kpi-definition.md, and business-glossary.md

## When Improving Documentation

- Add depth, not breadth - improve existing templates before adding new ones
- Remove empty or redundant sections rather than leaving placeholders
- Keep the total template count manageable (adding a template has a maintenance cost)
- Test that links between files resolve correctly
- Verify the README accurately reflects the current repo state
