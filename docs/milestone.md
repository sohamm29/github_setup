# Milestones

Milestones group issues/PRs targeted at a release. **One milestone per upcoming release, named after the release tag.**

## Convention

- Name = next release tag: `v1.4.0` (not "Q3 goals" or "Sprint 12").
- Optional due date = planned release date.
- Description = one-line theme of the release.

## Workflow

1. After releasing `v1.3.0`, create the milestone for the next version (`v1.4.0`, or `v2.0.0` if breaking work is planned).
2. Assign every accepted issue/PR to a milestone during triage. Unplanned work stays milestone-less until accepted.
3. Milestone progress bar = release readiness. Scope creep is visible: move items out rather than delaying the release.
4. When the release tag is published, close the milestone. Move any unfinished items to the next one.

## CLI

```bash
# create
gh api repos/{owner}/{repo}/milestones -f title="v1.4.0" -f description="Auth revamp" -f due_on="2026-08-01T00:00:00Z"

# assign an issue
gh issue edit 42 --milestone "v1.4.0"

# close (state=closed) by number
gh api -X PATCH repos/{owner}/{repo}/milestones/3 -f state=closed
```

## Rules of thumb

- If an issue has no milestone, it is not committed work.
- Never rename a milestone to "move" a release — close it and create the new one.
- RCs (`v1.4.0-rc.1`) share the milestone of the final release.
