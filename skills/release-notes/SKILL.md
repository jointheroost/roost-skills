---
name: release-notes
description: Write release notes from the merged pull requests of a GitHub repository since the last release or tag. Use it when the person asks for release notes, a changelog, or a summary of what shipped.
license: Apache-2.0
metadata:
  version: "1.0.0"
  category: coding
---

# Release notes

Write release notes that tell users what changed and why it matters to them.

## Gather the changes

1. Find the range. Use the range the person gives. Else use the pull requests merged since the newest release or tag.
2. List the merged pull requests in that range. Use the GitHub tools of the person's connected GitHub account, or `gh` on a node:

   ```sh
   gh pr list --state merged --base main --search "merged:>=2026-11-01" --json number,title,body,labels,author,mergedAt --limit 200
   ```

3. Read each title and body. Skip pull requests that only change tests, CI, or formatting, unless the person asks for every change.

## Group the changes

Use these groups, in this order. Leave out an empty group.

- **New:** features a user can see or use.
- **Changed:** behavior that is different now.
- **Fixed:** bugs that users could hit.
- **Removed:** things that are gone. Say what to use instead.
- **Security:** fixes for security problems. Do not give details that help an attacker.

## Write each line

- Start with what the user gets, not with what the code does: "Bots can read skill files" and not "Add read_skill_file handler".
- One line per change. Add the pull request number at the end: `(#123)`.
- Join related pull requests into one line.
- Mark a breaking change with **Breaking:** at the start, and say what the user must do.

## Before you finish

- Check that every breaking change has a clear next step.
- Give the notes to the person as a draft. Do not publish a release unless they ask.
