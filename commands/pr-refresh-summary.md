ultrathink - refresh PR summary to comprehensively reflect all PR changes while adhering to the repository's PR template structure.

## COMMIT FILTERING (CRITICAL)
Only include changes that originated from THIS PR branch, not merged content from upstream branches:

1. **Filter merge commits**: Exclude commits that are merge commits or came from other feature branches
2. **Author focus**: Include only commits made by the current author/contributor for this specific PR  
3. **Scope validation**: Exclude files/changes from unrelated feature work (different ticket numbers, functional areas)
4. **PR reference detection**: Commits with # numbers like #1866, #1938, #1926, #1865 are from other merged PRs - exclude these
5. **Verify boundaries**: When uncertain, confirm which changes belong to this PR's original scope vs merged dependencies

## TEMPLATE ADHERENCE
Structure the summary according to repository standards:

1. **Locate template**: Check for PR template files (.github/pull_request_template.md, etc.)
2. **Match structure**: If template exists, align PR description sections exactly with template format
3. **Preserve content**: Keep existing custom content that fits within the template structure
4. **Populate sections**: Fill template sections based on the filtered PR changes identified above

**Goal**: Generate an accurate PR summary that reflects only the work done in this specific PR, formatted according to the repository's expected structure to avoid misleading reviewers.
