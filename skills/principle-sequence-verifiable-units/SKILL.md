---
name: principle-sequence-verifiable-units
description: Sequence multi-step code changes and commit or PR boundaries into coherent, verifiable units sized for human review. Apply when planning migrations, sweeps, or delivery involving components or business logic.
---

# Sequence Verifiable Units

Choose boundaries by review effort and a meaningful verification result. A unit can span several files or consumers that must change together.

## Review size

- Count added plus deleted lines, never the net difference. Assess commits individually and a proposed PR against its actual base.
- For component or business-logic changes, target at most 400 changed lines per commit and fewer than 1000 changed lines per PR.
- During normal work, the user reviews every PR. These sizes guide reviewability; explain a justified exception in the review package rather than splitting a coherent change artificially.
- During an explicitly authorized Sleep Mode or other more autonomous run, enforce these limits strictly. Split into coherent verified units. If that is not possible, pause the affected work before exceeding the limit and report the reason.
- Translations and repetitive configuration may exceed the limits when they remain easy to inspect and do not alter behavior. Configuration that changes behavior is subject to the code limits. In mixed diffs, report exempt repetitive changes separately from code changes; do not use the exception to hide logic or behavior changes.

## Execution and delivery

- Establish the relevant baseline and choose a check that can demonstrate each unit's outcome.
- Verify the unit before starting work that depends on it. Resolve new failures first; distinguish evidenced baseline failures from regressions.
- Do not require a check after every edit. Updating a signature and its consumers together can be one unit. Planned isolated migration states do not require temporary compatibility just to keep each intermediate file compiling.
- Use meaningful behavior checks and applicable static checks. Do not add trivial tests merely to give every unit a test.
- Keep commits and proposed PRs coherent and reviewable. Do not automatically rebase, rewrite history, create failing-test-only commits, or manufacture independent PRs whose dependencies make them misleading to review.
- Preserve explicit human checkpoints. Size limits and verification do not grant permission to commit, open PRs, publish, merge, or activate autonomous mode.

Sleep Mode remains local-only under its existing contract. Apply the PR size limit to a planned delivery group without opening a PR. Passing checks is evidence for review, not human approval.
