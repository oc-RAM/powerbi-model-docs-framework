# Keeping Documentation Updated

Documentation is only useful if it reflects the current state of the model. This guide covers practical strategies for keeping your documentation current without creating excessive overhead.

## When to Update

Update documentation when any of these happen:

| Event | What to Update |
|-------|---------------|
| New measure added | measure-catalog.md |
| Measure DAX changed | measure-catalog.md, release-notes.md |
| Table added or removed | table-inventory.md, relationship-map.md |
| Column added or renamed | column-dictionary.md |
| Relationship changed | relationship-map.md |
| Report page added | report-page-inventory.md |
| KPI target changed | kpi-definition.md, release-notes.md |
| Power Query logic changed | power-query-docs.md |
| Data source changed | source-inventory.md |
| Refresh schedule changed | refresh-deployment-notes.md |
| Design decision made | issue-decision-log.md |
| Business term clarified | business-glossary.md |
| Version published | release-notes.md |

## The Update Habit

The most effective approach is to update documentation **in the same working session** as the model change.

1. Make the change in Power BI Desktop
2. Before publishing, update the relevant template files
3. Add a release notes entry
4. Publish the model and commit the documentation

If you separate model changes from documentation updates, the documentation will drift.

## Minimum Viable Updates

Not every change requires a comprehensive documentation review. Match the update to the change:

| Change Size | Documentation Update |
|------------|---------------------|
| Bug fix (no structural change) | Release notes entry only |
| New measure | Measure catalog entry + release notes |
| New report page | Report page inventory entry + release notes |
| Renamed column | Column dictionary update + release notes |
| New data source | Source inventory + table inventory + release notes |
| KPI target change | KPI definition update + release notes |

## Quarterly Review

Every quarter (or at whatever cadence fits your team), do a brief documentation review:

1. Open each template file
2. Verify that the content matches the current model
3. Remove entries for things that no longer exist
4. Add entries for things that were missed
5. Update the "Last Updated" date on each file

This catch-up review should take 30-60 minutes for a model documented with this framework.

## Signs Your Documentation Has Drifted

- Release notes stopped being updated months ago
- Measure catalog has measures that no longer exist in the model
- New tables appear in the model that are not in the table inventory
- Stakeholders reference KPI targets that do not match the KPI definition file
- A new team member reads the docs and finds them inaccurate

## Using Claude Code

If you use Claude Code, the following skills can help:

- **review-documentation** - Compares your docs against the model and flags inconsistencies
- **validate-completeness** - Checks whether all required templates are present and filled in
- **update-release-notes** - Generates a formatted release entry

See [claude-code-integration.md](claude-code-integration.md) for setup details.

## Tips

- Keep updates small and frequent rather than large and infrequent
- Use "Last Updated" dates on each file to spot stale documentation
- If a file has not been updated in 3+ months, review it during your next model change
- Treat documentation as part of the definition of done for any model change
