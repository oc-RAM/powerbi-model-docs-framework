# Maintaining the Framework

This guide is for maintainers of the powerbi-model-docs-framework repository itself - not for users documenting their own models. It covers how to evolve the framework responsibly.

## Adding a New Template

Before adding a template, verify that:

1. The documentation need is common enough to justify a reusable template (not specific to one project)
2. The need is not already covered by an existing template
3. The template adds clear value that justifies the maintenance cost

### Steps

1. Create the template file in `templates/` using kebab-case naming (e.g., `rls-documentation.md`)
2. Follow the existing template structure:
   - Summary table at the top (Model Name, Last Updated, etc.)
   - Usage notes in blockquotes (`>`)
   - Main content in markdown tables
   - Optional sections marked with `<!-- Optional -->`
3. Add a corresponding filled-in example in `examples/support-operations-analytics/`
4. Update `templates/README.md` to include the new template in the index and adjust the recommended starting set if appropriate
5. Update the `CHANGELOG.md`
6. If a Claude Code skill references the template list (e.g., `validate-completeness`), update the skill

### Template Structure Pattern

Every template should follow this pattern:

```markdown
# [Template Title]

> Remove these blockquote instructions when filling in this template.

## Summary

| Field | Value |
|-------|-------|
| Model Name | |
| Last Updated | |

[Main content sections with tables]

## Notes

-
```

## Updating the Example Project

When templates change, update the example to match:

- If a template gains a new section, add the section to the example file with realistic content
- If a template section is removed, remove it from the example
- If a template is added, create the corresponding example file
- Keep the example content consistent - all files should reference the same tables, measures, and business terms

## Updating Skills

When templates change in ways that affect skills:

- `create-model-docs` - Update the template list if templates are added or removed
- `validate-completeness` - Update the expected file list and section checks
- `generate-measure-catalog-entry` - Update if the measure-catalog format changes
- `create-template-from-pattern` - Update if template conventions change

Test skills after changes to verify they still produce correct output.

## Avoiding Bloat

The framework should stay lean. Resist the urge to add:

- Templates for edge cases that affect < 10% of users
- Sections that duplicate information available in other templates
- Guides that explain concepts already well-documented elsewhere
- Skills that solve problems users encounter once

### When NOT to Add a Template

- The need is specific to one industry or one company
- The content would be better as a section within an existing template
- The template would be empty for most projects
- Adding it increases the barrier to entry for new users

### When to Remove Content

- A template section is consistently left empty by users
- A guide duplicates advice given in another guide
- A skill does not solve a real repeated task
- An example file adds complexity without adding clarity

## Managing Contributions

When reviewing pull requests:

1. **Check scope.** Does the change align with PROJECT_SCOPE.md Is it within the non-goals
2. **Check public safety.** No proprietary content, no client names, no company-specific material.
3. **Check consistency.** Does the change follow existing naming conventions, template structure, and writing style
4. **Check the example.** If a template changed, did the example update too
5. **Check skills.** If templates changed, do the skills still work correctly
6. **Check cross-references.** Do links between files still resolve

## Release Process

1. Collect changes since the last release
2. Update `CHANGELOG.md` with a new version entry
3. Update `ROADMAP.md` if completed items can be moved from planned to done
4. Tag the release on GitHub
5. Write a brief release description summarizing changes

## Versioning

| Change Type | Version Bump | Example |
|------------|-------------|---------|
| New templates, new guides, new skills | Minor (0.1 -> 0.2) | Added rls-documentation template |
| Bug fixes, typo corrections, formatting | Patch (0.1.0 -> 0.1.1) | Fixed broken link in measure-catalog |
| Breaking changes to template structure | Major (0.x -> 1.0) | Restructured measure-catalog format |

## Long-term Health

- Review the roadmap quarterly and update priorities
- Monitor GitHub issues for recurring requests
- Periodically re-read the framework from a newcomer's perspective
- Keep the README accurate and up-to-date
- Respond to contributions promptly, even if the answer is "not in scope"
