---
name: principle-make-operations-idempotent
description: Prevent duplicate effects and unsafe recovery where retries, duplicate events, concurrent attempts, or partial execution are concrete possibilities. Use for affected commands and processing flows, not blanket hardening of every state change.
---

# Make Operations Idempotent

Make retrying the same logical operation safe where repetition or interruption is a real risk. A deliberate new operation may legitimately produce another effect.

## Establish the operation boundary

- Identify what makes two attempts the same operation, which effects must occur once, and what the caller should observe after a retry.
- Determine where retries, duplicate delivery, concurrency, or partial execution can actually occur. Do not add preventive infrastructure to unrelated small features.
- Keep operation identity scoped to the relevant actor and intent. Do not collapse distinct requests merely because their payloads match, or reuse an identity for changed intent without detecting the conflict.

## Reuse concrete guarantees

- Prefer existing transactions, uniqueness constraints, provider idempotency support, or established operation records when they cover the affected boundary.
- Account for concurrent attempts. Checking for existence before creating an effect is insufficient if another attempt can pass the same check; use the existing atomic guarantee appropriate to the storage or provider.
- Identify partial states and the evidence needed to resume or reconcile them. A local transaction does not make an external side effect atomic. Do not mark an operation complete without evidence of its required effects.
- When an external outcome is unknown, inspect or reconcile its state before another attempt. Retry only when available guarantees make that attempt safe; otherwise report the uncertainty and pause the affected action. Preserve authorization and high-impact correction gates.
- Propose new infrastructure, dependencies, or broader changes separately when the current task cannot safely accommodate them. Do not introduce universal retry wrappers or automatic cleanup of uncertain state.

## Verify the relevant failure modes

- Check the normal result, a repeated attempt with the same identity, and a deliberate new operation that must remain distinct.
- Exercise meaningful interruption points and concurrent attempts where the risk exists. Verify observable effects and returned status, not merely that the handler returns successfully.
- Keep verification proportional to the affected flow. Do not simulate every possible interruption or claim exactly-once effects beyond the guarantees actually established.

Report unresolved outcomes and unverified recovery paths explicitly. Idempotency does not authorize repeated external actions or replace permission checks.
