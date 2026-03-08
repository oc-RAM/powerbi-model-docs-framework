---
name: update-release-notes
description: "Use this skill when the user wants to add a new entry to the release notes for a Power BI model or documentation project. Triggers when the user says things like 'add release notes', 'update the release notes', 'log this change', 'record this release', or 'add a changelog entry'. Appends a formatted release entry to the release-notes.md file."
tools: Read, Write, Edit, Glob
---

# Update Release Notes

Appends a new release entry to a release-notes.md file following the framework's standard format.

## Prerequisites

- The user describes what changed (required)
- Optionally: version number, release date, released by, impact notes

## Workflow

1. **Gather release information** from the user:
   - What changed (required - list of changes)
   - Version number (optional - auto-increment from last entry if not provided)
   - Release date (optional - default to today)
   - Released by (optional)
   - Impact on existing reports or users (optional)
   - Additional notes (optional)

2. **Find the release-notes.md file**:
   - Check the path provided by the user
   - Or search the current directory and common documentation paths

3. **Read the existing file** to:
   - Determine the last version number (for auto-incrementing)
   - Find the correct insertion point (new entries go at the top of the Releases section, after the Summary table)

4. **Determine the version number**:
   - If the user provided one, use it
   - If not, auto-increment from the last version:
     - New measures, pages, or features -> minor bump (1.1 -> 1.2)
     - Bug fixes or formatting -> patch bump (1.1 -> 1.1.1)
     - Breaking changes -> major bump (1.x -> 2.0)

5. **Format the entry**:

   ```markdown
   ### [Version] - [Short Title]

   **Released**: [Date]
   **Released By**: [Name]

   **Changes**:

   - [Change 1]
   - [Change 2]

   **Impact**:

   - [Impact description, or "No impact on existing reports"]

   **Notes**:

   - [Additional context]

   ---
   ```

6. **Insert the entry** at the top of the Releases section (after the `## Releases` heading, before the previous first entry).

7. **Update the Last Updated date** in the Summary table.

## Output

The release-notes.md file updated with the new entry at the top of the releases list.

## Rules

- Follow the release-notes.md template format exactly
- Most recent entry always appears first (reverse chronological)
- Include a horizontal rule (`---`) after each entry
- Write changes as actionable descriptions ("Added X measure", "Fixed Y calculation", not "Changes were made")
- If impact is unclear, write "No impact on existing reports" rather than leaving it blank
- Do not modify existing entries unless the user explicitly asks
