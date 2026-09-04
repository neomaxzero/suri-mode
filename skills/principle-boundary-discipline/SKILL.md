---
name: principle-boundary-discipline
description: Place validation, error handling, and data conversion according to trust boundaries and business guarantees. Use when changing input handling or adapters, or evaluating apparently redundant guards; never assume internal types make all runtime checks unnecessary.
---

# Boundary Discipline

Establish which guarantees each part of the system may rely on. Centralize duplicated checks only when their guarantees remain valid; do not trust internal code unconditionally.

## Identify the guarantee

- Trace where the data originates, who can modify it, and which entry points can reach the operation. Include external APIs, configuration, persisted data, public functions, and separate trust boundaries.
- Distinguish representation checks from business rules. A valid number does not establish available stock, sufficient balance, permission, or a valid state transition.
- Parse and validate untrusted input at the relevant entry point, converting it into a useful domain representation. Typed declarations or casts alone do not prove that runtime input was checked.

## Preserve checks that remain necessary

- Enforce business rules where the authoritative decision is made. Recheck when state changes or another trust boundary invalidates an earlier guarantee.
- For decisions coupled to mutable state, preserve the required atomicity or transactional guarantee. A repeated check alone may still race with another writer.
- Before removing a guard, establish that every relevant path provides the same guarantee and that mutation, elapsed time, persistence versions, or alternate callers cannot invalidate it. If that evidence is missing, keep the check or investigate further.
- A repeated condition is not automatically redundant. Keep legitimate validation, authorization, and compatibility handling even when the same data was checked elsewhere.

## Keep the boundary understandable

- Prefer domain concepts over unnecessary transport, storage, or framework details in domain-facing interfaces. Preserve existing public contracts unless changing them is within the approved scope.
- Keep business decisions out of mechanical framework wiring when separating them simplifies the current change. Prefer pure transformations where useful, but do not extract functions or add adapters merely because purity is possible.
- Propagate or translate errors where there is enough context to handle them meaningfully. Do not silently swallow failures or turn invalid input into apparent success.
- Verify the affected entry paths, relevant invalid inputs, and business conditions. Scope changes to the requested behavior; this principle does not authorize a validation sweep or architectural rewrite.
