# The Process (Workflow)

This is the standard operating procedure for work in an isolated agent environment.
It defines required outcomes, while allowing each agent runtime to choose its own local execution mechanics.

## 1. Discovery
- **Check for Work**: Query GitHub for actionable reviews and unclaimed tasks.
- **Priority 1**: Review requests (unblock others first).
- **Priority 2**: Open, unclaimed task issues.
- Labels are optional metadata, not a hard protocol dependency.

## 2. Claiming (Synchronization Point)
Since you cannot "talk" to other agents, the GitHub Issue assignment is your lock:
1.  **Claim**: assign yourself to one task issue.
2.  **CAS Verify**: Immediately re-read the issue. If another agent's name appears in the assignees list alongside yours, you have a collision. Remove yourself and pick a different task.

## 3. Execution (Private Sandbox)
1.  **Sync**: `git pull origin main`.
2.  **Branch**: `git checkout -b collab/task-T-<id>`.
3.  **Work**: Read the issue. Implement. Run tests.
4.  **Commit**: `git commit -am "[collab] T-<id>: <summary>"`.
5.  **Push**: `git push -u origin collab/task-T-<id>`.

## 4. Submission
1.  **PR**:
    ```bash
    gh pr create --fill
    ```
    Then assign a reviewer per Section 6 (any active non-self agent, or `needs-human-review` if none).
2.  **Update State**:
    - Optional: update labels/comments if the project uses them.

## 5. Reviewing
1.  **Fetch**: `gh pr checkout <pr-number>`.
2.  **Verify**: Run tests. Read diffs.
3.  **Decide**:
    - **Pass**: `gh pr review --approve --body "LGTM"`
    - **Fail**: `gh pr review --request-changes --body "Fix X, Y, Z"`

## 6. Reviewer Assignment
To prevent deadlocks, reviewer selection follows a dynamic algorithm:

1. **Discover active agents**: Query recent GitHub activity (commits, PR comments, issue assignments) to build a list of known agents.
2. **Select reviewer**: Pick any active agent that is NOT the PR author. If multiple candidates exist, prefer the agent with the fewest currently-assigned reviews.
3. **Timeout**: If the assigned reviewer has no activity for 1 hour, re-assign to another active agent.
4. **Escalation**: If no other agent is available (single-agent scenario), label the PR `needs-human-review` for HITL escalation.

**Key constraint**: An agent CANNOT review its own PR. In a single-agent project, all PRs require human review.

## 7. Merging
- If you are the **Author** and receive an **Approval**:
- `gh pr merge --squash --delete-branch`
