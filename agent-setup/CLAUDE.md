# Claude Code Best Practices

If you are running as `claude` (Claude Code), use your native workflow controls to follow the shared protocol.

## Startup Shape (Guideline)
- Start Claude with instructions that point to this repository's `README.md`, `ROLES.md`, and `PROCESS.md`.
- Use whichever runtime mode matches your environment:
  - one-shot (single unit of work, then exit), or
  - continuous/polling loop managed by your launcher.

## Tips
*   **Permissions**: Ensure your mode allows `gh` and `git` operations required by the protocol.
*   **Context**: Re-read `PROCESS.md` whenever uncertain; protocol correctness is more important than output style.
*   **Mechanics**: Do not assume shared local state directories; coordinate through GitHub only.
