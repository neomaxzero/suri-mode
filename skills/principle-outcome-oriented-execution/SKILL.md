---
name: principle-outcome-oriented-execution
description: Guide planned rewrites and migrations toward a verified replacement, avoiding speculative backward compatibility. Use when replacing an existing path with identified consumers and explicit verification boundaries, not for ordinary bugs or small features.
---

# Outcome-Oriented Execution

Complete the agreed replacement and retire the superseded path. Backward compatibility needs a concrete consumer or delivery requirement.

## Define the migration boundary

- Establish the intended end state, affected consumers, and delivery boundary before changing the old contract.
- Inspect callers and relevant external contracts. A lack of visible local callers alone does not prove an interface is unused. Investigate material uncertainty instead of automatically adding compatibility or deleting the old path.
- Update affected consumers together and remove the superseded implementation within the authorized scope. If completing the migration requires wider changes, surface that boundary rather than silently expanding the task.

## Require a reason for compatibility

- Do not add aliases, wrappers, fallbacks, dual APIs, or dual data paths solely to preserve old implementation choices, satisfy hypothetical consumers, or keep every intermediate edit compiling.
- Preserve compatibility when evidence shows consumers cannot migrate together, a public contract remains in force, or staged deployment requires old and new versions to coexist.
- When a compatibility path is necessary, identify the consumer or delivery constraint and the condition for retiring it. Do not promise removal before that condition can be verified.

## Verify at meaningful boundaries

- Incomplete intermediate states are acceptable only inside an agreed, isolated, reversible migration boundary. Do not break production, shared integration points, or explicit human review checkpoints to simplify implementation.
- Keep useful checks for the areas being migrated. Do not create throwaway compatibility merely to pass a check at every edit.
- Before delivery, verify the integrated replacement, affected consumers, and required static and runtime behavior. Broaden testing only for failures, changed dependencies, or unresolved risk.
- Confirm that obsolete paths were retired where authorized. Report remaining compatibility and its reason, along with any unverified behavior.

This principle does not authorize a rewrite, expand a small task, or override diagnostic approval gates. Use it after the migration scope is established.
