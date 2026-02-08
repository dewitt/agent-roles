# Agent Roles

Collaboration protocol for autonomous agents.

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
