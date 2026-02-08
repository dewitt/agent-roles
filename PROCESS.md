# Workflow

Standard operating procedure for isolated agents.

## 1. Discovery
- **Check**: Query GitHub for actionable reviews and unclaimed tasks.
- **Priority**:
  1.  Review requests (unblock others).
  2.  Open, unclaimed task issues.
- Labels are optional metadata.

## 2. Claiming
Issue assignment is the synchronization lock.
1.  **Claim**: Assign yourself to the task issue.
2.  **Verify**: Immediately re-read the issue. If another agent is also assigned, remove yourself and pick a different task.

## 3. Execution
1.  **Sync**: Pull the default branch.
2.  **Branch**: Create a feature branch. Follow the project's existing branch naming convention if one exists. Otherwise, use a short descriptive name (e.g., `fix-login-bug`, `add-search-endpoint`).
3.  **Work**: Read the issue, implement, and test.
4.  **Commit**: Write clear commit messages. Follow the project's existing commit convention if one exists.
5.  **Push**: Push your branch to the remote.

## 4. Submission
1.  **PR**:
    ```bash
    gh pr create --fill
    ```
    -   **Identity**: Include your agent name in the title or body (e.g., `[Gemini]`) to distinguish from other agents sharing the account.
    -   Assign a reviewer per Section 6 (active non-self agent or `needs-human-review`).
2.  **Update**: Optional label/comment updates.

## 5. Reviewing
1.  **Fetch**: `gh pr checkout <pr-number>`
2.  **Verify**: Run tests and read diffs.
3.  **Decide**:
    - **Pass**: `gh pr review --approve --body "LGTM"`
    - **Fail**: `gh pr review --request-changes --body "Fix X, Y, Z"`

## 6. Reviewer Assignment
To prevent deadlocks:

1.  **Discover**: Query recent activity (commits, comments) for active agents.
2.  **Select**: Pick an active agent that is not the PR author. Prefer fewest active reviews.
3.  **Timeout**: If no activity for 1 hour, re-assign.
4.  **Escalation**: If no other agent is available, label `needs-human-review`.

**Constraint**: Do not review your own PR. If sharing a GitHub account, check the PR title/body for your agent identity before reviewing.

## 7. Merging
- If **Author** and received **Approval**:
  - `gh pr merge --squash --delete-branch`