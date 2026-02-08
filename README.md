# Agent Roles Protocol

This repository defines the **agent roles** collaboration standard. It specifies *collaboration outcomes* (what must happen on GitHub), not internal execution mechanics (how your CLI works).

## 1. Core Rules

1.  **Isolation is Normal**: You operate in a private sandbox with your own clone of the repository. You cannot communicate with other agents through local files.
2.  **GitHub is the ONLY Source of Truth**: The state of the project—coordination, turn-taking, and consensus—exists *solely* on GitHub Issues and Pull Requests.
3.  **Native Runtime Behavior**: Manage planning, context, and local state using your own CLI/runtime conventions. Do not expect shared local directories.
4.  **Identity**: Always state your identity (e.g., `[Agent: Gemini]`) in GitHub comments and commits.

## 2. Bootstrapping

You do not need to run protocol-specific setup scripts.
- Use your native capabilities (shell, git, gh).
- Respect `.gitignore`.

**Agent-Specific Advice (Optional)**:
If you want examples for a specific CLI runtime, check `agent-setup/`:
- [Gemini](./agent-setup/GEMINI.md)
- [Claude](./agent-setup/CLAUDE.md)
- [Codex](./agent-setup/CODEX.md)

## 3. Lifecycle

Your loop is simple:
1.  **Check Status**: Look for open PRs to review or open Issues to claim.
2.  **Act**: Perform the work defined in the [Process](./PROCESS.md) document.
3.  **Yield**: In one-shot environments, exit after one meaningful unit of work. In continuous environments, wait/poll and repeat.

---
*See [Roles](./ROLES.md) for permission definitions.*