# Pull Requests Conventions

**Table of Contents:**
- [Pull Requests Conventions](#pull-requests-conventions)
- [Body Conventions](#body-conventions)
- [Assignees](#assignees)
- [Comments Etiquette](#comments-etiquette)
  - [Resolving comments](#resolving-comments)
- [Merge](#merge)
  - [Merge Commit Message](#merge-commit-message)


# Body Conventions

In the body, we try to provide as much information about the changes as we can.

This means:

- Filling up the description of the changes
- Provide Before / After screenshots or videos
- Provide links to related discussions / decisions taken in Slack or Notion
- Provide a link to the Figma page in case of UI changes

# Assignees

In general, the PR Owner is the assignee of that PR.

# Comments Etiquette

- Assume competence and good intent.
- Be kind and praise good code.
- The code belongs to the team, use team language (we, our) instead of personal language (me, you).

## Resolving comments

- All comments should be resolved before merging.
- This could be as easy as reacting to a comment and mark it as done after making the proposed change; or engaging in a discussion about the comment.
- Both the owner of the PR and the reviewer making a comment have the ability to `resolve` comments.
- In the case that you find a non-trivial mistake in the code after it has been approved, you should request a new round of reviews.

# Merge

Once the PR:

* Is updated with the head branch
* Is approved by at least one reviewer (ideally 2 or more)
* Has all the green checks in the CI actions
* Has all its conversations marked as resolved

It's ready to merge. Anyone (Owner and reviewers) can merge it at this point.

## Merge Commit Message

We enforce the `Squash and Merge` feature when merging PRs.

The commit message of the merge should contain the PR Title and the PR number. Example: `Handle Race Condition in SignIn flow (#554)`

The commit description message should include the PR body description, and avoid intermediate commit messages without too much value (examples: `run formatter`, `fix tests`).