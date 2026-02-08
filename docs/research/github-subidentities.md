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
- **Author vs. Committer**: Git distinguishes between the author (`GIT_AUTHOR_NAME`) and the committer (`GIT_COMMITTER_NAME`). Agents could set themselves as the author while keeping the human user as the committer, preserving the contribution graph while attributing the work.

### 2. GitHub API Interactions (The Platform Layer)

Actions performed via the GitHub API (creating Issues, PRs, Comments) are authenticated using a Personal Access Token (PAT).

- **Mechanism**: The API infers the "actor" from the token.
- **Result**: All artifacts created via the API are attributed to the owner of the token. There is no "sub-identity" or "on-behalf-of" parameter for standard user accounts.
- **Fine-Grained PATs**: Do not provide identity separation; they only scope permissions. All actions are still attributed to the token owner.

### 3. Advanced Mechanisms

- **GitHub Apps**: Apps can act as independent identities, authoring commits as `app-name[bot]`. This provides the strongest separation but requires installing and managing an App, which adds significant overhead compared to a simple PAT workflow.
- **Co-Authored-By Trailers**: Adding `Co-authored-by: Agent Name <email>` to commit messages is a standard way to attribute multiple authors. GitHub renders these with profile links if the email resolves to a user. This is already supported by the platform.

## Recommendations

1.  **Tier 1: Minimal Friction (Recommended)**
    - **Issues/PRs**: Continue using text prefixes (e.g., `[Gemini]`) in titles and bodies. Simple, portable, zero-setup.
    - **Commits**: Configure `git config user.name "AgentName (via Human)"` for agent sessions. This makes `git log` visually distinct.
    - **Co-Authoring**: use `Co-authored-by` trailers when collaborating with other agents or humans.

2.  **Tier 2: Robust Attribution (Optional)**
    - **Separate Author/Committer**: Set `GIT_AUTHOR_NAME` to the agent and `GIT_COMMITTER_NAME` to the human user for precise attribution in git history.
    - **GitHub Apps**: Develop a lightweight App for rigorous identity separation if the project scale justifies the complexity.

## Conclusion

GitHub does not support native sub-identities for a single user account in the UI. The current text-based convention combined with git author configuration offers the best balance of simplicity and clarity.