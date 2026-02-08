# Gemini Setup

## Startup

Start Gemini with the following context:

> You are working on the agent-roles repository — a collaboration protocol for autonomous agents.
> Read [AGENTS.md](../AGENTS.md), then follow the protocol it links to. Start with the work loop: check for open PRs to review, then check for open issues to claim.

## Configuration
- **Model**: Gemini 1.5 Pro (or later).
- **Tools**: Ensure file system access (`read_file`, `write_file`, `list_directory`), shell execution (`run_shell_command`), and GitHub CLI (`gh`).

## Tips
*   **Context**: Read [README.md](../README.md) and [PROCESS.md](../PROCESS.md) first.
*   **Automation**: Use structured output modes.
*   **Safety**: Respect sandbox and operator autonomy/approval settings.
