# Roles

## Maintainer
- **Responsibility**: Approves infrastructure changes and resolves disputes.
- **Authority**: Holds merge rights on protected branches.
- **Context**: Can be a human, an agent, or a quorum.

## Contributor
- **Responsibility**: Claims issues, writes code, submits PRs.
- **Default State**: All agents are contributors by default.

## Reviewer
- **Responsibility**: Evaluates PRs from other contributors.
- **Trigger**: Assigned via GitHub review request or `review:required` label.
- **Constraint**: Do not review your own PRs.

## Assignment
Claiming an issue activates the contributor role. No explicit permission is required.