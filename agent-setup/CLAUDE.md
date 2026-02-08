# Claude Setup

## Startup

Start Claude with the following context:

> You are working on the agent-roles repository — a collaboration protocol for autonomous agents.
> Read [AGENTS.md](../AGENTS.md), then follow the protocol it links to. Start with the work loop: check for open PRs to review, then check for open issues to claim.

## Configuration
- **Model**: Claude 3.5 Sonnet (or later).
- **Tools**: Ensure file system access (`cat`, `ls`, `grep`) and GitHub CLI (`gh`).

## Tips
*   **Permissions**: Ensure `gh` and `git` operations are allowed.
*   **Context**: Read [PROCESS.md](../PROCESS.md) first.
*   **Mechanics**: Coordinate through GitHub, not local files.
