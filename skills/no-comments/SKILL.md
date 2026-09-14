---
name: no-comments
description: Keep authored code free of explanatory comments and preserve non-obvious rationale in commit or PR history. Apply to comments in the requested code changes or an explicit comment cleanup, not a repository-wide refactor.
---

# No Comments

Prefer code without explanatory comments. Preserve decisions and constraints that the code cannot express in the associated commit or PR history, rather than maintaining inline explanations.

## Author within the current scope

- Do not add explanatory comments to code. Prefer clear names and straightforward structure, but do not invent abstractions, wrappers, or broad refactors just to replace prose.
- Put non-obvious rationale, rejected alternatives, and constraints in the commit message or PR description associated with the change. Identify the affected symbol or path and cite relevant evidence so later investigation can find the reason.
- This policy does not require deleting comments from every file touched. Limit cleanup to the requested scope and preserve unrelated user edits.

## Preserve before removing

- Before deleting an existing comment with useful information, inspect its claim and check whether the associated history already preserves it. Redundant narration of obvious code need not be copied into history.
- Preserve useful reasons and constraints in an authorized commit or PR before removing the comment, or in the same authorized commit that removes it. Do not invent historical intent or describe an uncertain claim as verified.
- If publication or commits are not authorized, prepare the proposed history text in the existing task record and retain the informative comment until that history preservation can occur. A local note alone is not Git history. Continue other authorized work without silently discarding the information.
- Investigate warnings before removal. Moving a constraint to history does not authorize changing the behavior it protects. If its validity is unresolved, preserve that uncertainty and the original evidence.

## Preserve functional and legal content

- Keep required license and attribution notices, generated-file markers used by tooling, and functional directives such as TypeScript or lint suppressions. They are not merely explanatory prose.
- Remove a suppression only when its underlying issue is resolved within scope and relevant checks pass. Do not convert comment cleanup into type hardening, architecture changes, or automatic suppression removal.
- Where comment syntax supplies metadata required by an API, compiler, documentation build, or other existing tool, establish its role before changing it and preserve required functionality.

## Verify and hand off

- Review the scoped diff for accidental code changes and loss of useful rationale. Run applicable checks when removing functional content or changing code; do not require runtime tests for plain comment deletion alone.
- Report meaningful retained exceptions and where useful rationale was preserved. Do not claim a commit or PR was updated unless it was.
- Work directly by default. A separate reviewer, architect, or model is not required; follow Suri's proportional review policy when actual uncertainty or impact warrants one.

The no-comments preference does not authorize commits, PR writes, broader cleanup, or loss of required notices. Preserve existing human checkpoints.
