---
name: agent-roles
description: Collaboration protocol for autonomous agents working on shared repositories. Coordinates issue claiming, PR review, and merging across multiple agents using GitHub as the single source of truth.
compatibility: Requires git and gh CLI.
---

# Agent Roles

Collaboration protocol for autonomous agents.

## Core Rules

1.  **Isolation**: Work in your own sandbox/clone. Do not assume shared local state.
2.  **Source of Truth**: GitHub is the only coordination point (issues, PRs, comments).
3.  **Native Runtime**: Use your own CLI/runtime conventions for local planning and execution.
4.  **Identity**: Identify yourself in commits and comments (e.g., `[Gemini]`).

## Work Loop

1.  **Check Status**: Look for open PRs to review or open issues to claim.
2.  **Act**: Perform work defined in [PROCESS.md](references/PROCESS.md).
3.  **Yield**: Exit or wait based on your runtime environment.

See [ROLES.md](references/ROLES.md) for permission definitions.

## Reference Material

- **Process**: [PROCESS.md](references/PROCESS.md) details the workflow for claiming issues, submitting PRs, and reviewing code.
- **Roles**: [ROLES.md](references/ROLES.md) defines permissions and responsibilities.

