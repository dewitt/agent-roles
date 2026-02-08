# Agent Roles

Collaboration protocol for autonomous agents.

## Why Agent Roles?

Autonomous agents often lack coordination mechanisms when working on shared codebases, leading to race conditions, context loss, and low-quality commits.

**Agent Roles** solves this by providing a minimal, decentralized framework for multiple autonomous AI agents (and humans) to collaborate without stepping on each other's toes. By defining explicit roles (Maintainer, Contributor, Reviewer) and a strict GitHub-centric workflow, it ensures high-quality contributions and conflict-free integration.

## Core Rules

1.  **Isolation**: Work in your own sandbox/clone. Do not assume shared local state.
2.  **Source of Truth**: GitHub is the only coordination point (issues, PRs, comments).
3.  **Native Runtime**: Use your own CLI/runtime conventions for local planning and execution.
4.  **Identity**: Identify yourself in commits and comments (e.g., `[Gemini]`).

## Startup

No protocol-specific setup scripts are required.
- Use native capabilities (shell, git, gh).
- Respect `.gitignore`.

**Runtime Guides**:
- [Gemini](./agent-setup/GEMINI.md)
- [Claude](./agent-setup/CLAUDE.md)
- [Codex](./agent-setup/CODEX.md)

## Work Loop

1.  **Check Status**: Look for open PRs to review or open issues to claim.
2.  **Act**: Perform work defined in [PROCESS.md](./PROCESS.md).
3.  **Yield**: Exit or wait based on your runtime environment.

See [ROLES.md](./ROLES.md) for permission definitions.

## Adopting Agent Roles

To use this protocol in your own project, add an `AGENTS.md` file to your repository root with:

```
This project uses agent roles (https://github.com/dewitt/agent-roles). Please review the roles to contribute.
```

Agents that read `AGENTS.md` on startup will follow the linked protocol automatically.
