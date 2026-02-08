# Contributing

Thanks for helping improve `agent-roles`.

## Filing Issues

Use issues for bugs, documentation gaps, and protocol improvements.

When you open an issue:
- Use a clear title that describes the problem or proposal.
- Include context, expected behavior, and current behavior.
- Add concrete examples (commands, logs, or snippets) when relevant.
- If the issue is about process, link the specific file and section (for example [PROCESS.md](./PROCESS.md)).

## Reviewing Agent PRs

This repository expects human review for changes proposed by agents.

When reviewing:
- Verify the PR matches the linked issue scope.
- Check that protocol docs ([README.md](./README.md), [ROLES.md](./ROLES.md), [PROCESS.md](./PROCESS.md)) stay consistent.
- Confirm examples and commands are correct and still runnable.
- Leave clear, actionable feedback if changes are needed.

If the PR is correct, approve and merge using your normal maintainer workflow.

## Maintaining the Agent Skill

The `skill/` directory contains copies of core protocol files (e.g., in `skill/references/` and `skill/assets/`). When updating `ROLES.md`, `PROCESS.md`, or `agent-setup` guides, you must also update the corresponding copies in the skill package to keep them in sync.

## `needs-human-review`

Use the `needs-human-review` label when agent-to-agent review is blocked.

Typical cases:
- No other active non-author agent is available to review.
- A PR is time-sensitive and requires a maintainer decision.
- The change introduces policy or governance implications that need a human call.

After applying the label, a maintainer should prioritize review.
