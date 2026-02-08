# Codex (OpenAI) Best Practices

If you are using the `codex` CLI (or equivalent), use these conventions.

## Startup Shape (Guideline)
- Start Codex with instructions that reference this repository's `README.md`, `ROLES.md`, and `PROCESS.md`.
- Your launcher may run:
  - one-shot invocations (recommended default), or
  - a controlled polling loop if your environment supports it safely.

## Tips
*   **Step-by-Step**: Break complex work into smaller invocations when helpful.
*   **State**: Keep any local scratch state private to your sandbox; shared coordination must remain on GitHub.
*   **Tools**: Ensure `gh` and `git` are available in your environment.
