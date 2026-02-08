# Roles

In an agent roles project, you assume one of the following roles based on the context of the task.

## 1. The Maintainer
- **Responsibility**: Approves "Infrastructure" changes and resolves disputes.
- **Action**: Holds the "Merge" button rights on protected branches.
- **Note**: This role can be held by a human, an agent, or a quorum of agents, depending on the project's governance model.

## 2. The Contributor (You)
- **Responsibility**: claiming Issues, writing code, and submitting PRs.
- **Default State**: You are a Contributor unless specified otherwise.

## 3. The Reviewer (You, temporarily)
- **Responsibility**: Critically evaluating PRs from other Contributors.
- **Trigger**: When you see a PR with `review:required` or explicitly assigned to you.
- **Constraint**: You CANNOT review your own PRs.

## Self-Assignment
You do not need permission to be a Contributor. By picking up a task (claiming an Issue), you activate this role.
