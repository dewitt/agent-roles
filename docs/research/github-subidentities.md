# GitHub Sub-Identities Investigation

**Issue**: #19
**Date**: 2026-02-08

## Objective

Investigate whether GitHub supports "sub-identities" or ways to attribute actions (Issues, PRs, Comments) to specific agents (e.g., Gemini, Claude) operating under a single human user account.

## Findings

### 1. Git Commits (The Git Layer)

Git tracks authorship via `user.name` and `user.email` in each commit object. This is separate from GitHub authentication.

- **Mechanism**: Agents can configure `git config user.name "Gemini (via DeWitt)"` and `git config user.email "dewitt+gemini@example.com"` locally before committing.
- **Result on GitHub**:
    - If the email is **linked** to the GitHub account: The commit is attributed to the main user profile.
    - If the email is **unlinked**: The commit appears with the configured name (e.g., "Gemini (via DeWitt)") and a generic avatar (unless a Gravatar exists for that email). This provides visual distinction in the commit history.

### 2. GitHub API Interactions (The Platform Layer)

Actions performed via the GitHub API (creating Issues, PRs, Comments) are authenticated using a Personal Access Token (PAT).

- **Mechanism**: The API infers the "actor" from the token.
- **Result**: All artifacts created via the API are attributed to the owner of the token. There is no "sub-identity" or "on-behalf-of" parameter for standard user accounts.
- **Exceptions**:
    - **GitHub Apps**: Can act as independent bot identities. This requires installing an App, which is heavier than a simple PAT-based workflow.
    - **Separate Accounts**: Creating machine user accounts for each agent (e.g., `dewitt-gemini`) works but increases management overhead (multiple tokens, 2FA, etc.).

## Recommendations

1.  **Status Quo (Text Prefixes)**: Continue using text prefixes (e.g., `[Gemini]`) in titles and bodies for Issues and PRs. This is simple, portable, and requires no extra infrastructure.
2.  **Commit Attribution**:
    - Agents **should** configure `git config user.name "AgentName (via Human)"` for their sessions.
    - This makes the `git log` and GitHub commit history visually distinct, even if the PR author remains the human user.
3.  **Future Consideration**:
    - If rigorous attribution is needed, a "lightweight" GitHub App could be developed, but this deviates from the "minimal protocol" goal of `agent-roles`.

## Conclusion

GitHub does not support native sub-identities for a single user account in the UI. The current text-based convention is the best trade-off for simplicity. However, configuring `git user.name` per agent is a low-cost improvement for commit history clarity.
