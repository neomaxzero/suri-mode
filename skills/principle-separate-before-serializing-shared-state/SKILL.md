---
name: principle-separate-before-serializing-shared-state
description: Prevent lost updates when concurrent writers affect the same mutable state. Evaluate independent ownership before adding coordination, and preserve real shared invariants with existing atomic or transactional guarantees.
---

# Separate Before Serializing Shared State

Choose coordination from the ownership and invariants of the data. Separating genuinely independent writes can remove a conflict; genuinely shared state needs an appropriate concurrency guarantee.

## Identify the conflict

- Identify the writers, the shared write target, and the actual read-modify-write boundary. Different fields in one file still conflict when each writer replaces the whole file.
- Establish the invariant that must survive concurrent attempts, such as preserving both updates or preventing stock from going below zero.
- Determine whether concurrency spans tasks, processes, servers, or external services. Do not assume a lock in one process protects writers elsewhere.

## Choose a proportionate boundary

- Separate write targets only when the data is independently owned and combining it later preserves required consistency. Do not split one canonical balance, inventory, or other shared invariant merely to avoid a lock.
- When state must remain shared, reuse suitable existing atomic updates, conditional writes, transactions, or single-writer ownership. Locks are legitimate tools, not evidence of bad design by themselves.
- Check that the chosen guarantee covers all relevant writers and the full invariant. A transaction or lock name alone does not establish its isolation, lifetime, or coverage.
- Avoid check-then-write races and whole-object replacement that silently discards unrelated concurrent updates. Prefer the storage system's supported guarantee for the affected operation.
- Do not add distributed coordination or redesign ownership without a demonstrated need. Propose any prerequisite that expands the authorized scope separately.

## Verify the invariant

- Exercise meaningful overlapping attempts and inspect the final state for lost updates or invariant violations. Sequential success does not prove concurrency safety.
- Where the chosen mechanism introduces relevant failure behavior, check conflicts, interruption, or lock release proportionately. Reuse the existing retry policy; do not blindly retry an operation with an uncertain external effect.
- Preserve diagnostic and high-impact approval gates. Report the actual guarantee observed and any execution environments or failure cases left unverified.

Instructions to take turns are not concurrency control. This principle applies to concrete concurrent-write risks, not broad preventive refactoring.
