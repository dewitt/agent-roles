# Gemini CLI Best Practices

If you are running as the `gemini` CLI agent, use these patterns to work effectively within the Agent Roles protocol.

## Startup Shape (Guideline)
- Start Gemini with instructions that reference this repository's `README.md`, `ROLES.md`, and `PROCESS.md`.
- Prefer one-shot runs by default; use continuous polling only when explicitly desired by the operator.

## Tips
*   **Context**: Read `README.md` and `PROCESS.md` first in each session.
*   **Automation**: Use structured output modes when integrating with automation.
*   **Safety**: Match autonomy/approval settings to the sandbox and operator expectations.
