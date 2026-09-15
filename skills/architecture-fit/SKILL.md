---
name: architecture-fit
description: Review or guide code changes when ownership, dependency direction, shared contracts, cross-layer abstractions, or stable runtime boundaries materially affect whether a solution fits the existing architecture. Do not use for isolated implementation details with no architectural choice.
---

# Architecture Fit

Keep solutions aligned with the architecture already present. Treat functional correctness as necessary but insufficient.

## Establish the boundary

Before choosing an implementation, identify:

- The behavior or data that must change.
- The stable core that should remain unchanged.
- The layer that owns the variation.
- Existing operational properties to preserve, such as offline execution, persistence, synchronization, and compatibility.

Prefer evidence from the current data flow, public contracts, storage boundaries, and nearby conventions over abstract pattern preferences.

## Sketch only the decision that needs design

- For an explicit architecture-design request or a concrete structural choice, start with how the caller would use the proposed solution. Sketch only the types, signatures, ownership, or module boundaries needed to judge that choice.
- Use existing contracts and operational constraints as inputs. A short usage example or written sketch is usually enough; do not create production files with empty bodies or a full scaffold merely to present a design.
- Compare viable alternatives only when an unresolved question could materially change the design. Reuse established patterns when they fit, and stop exploring when the evidence is sufficient. Multiple models or competing prototypes are not mandatory.
- Explain the chosen boundary and its tradeoffs. For unfamiliar backend, database, or infrastructure choices, include the relevant guarantee and a concrete failure mode so the user can evaluate the proposal.
- A request to design or review does not authorize implementation. When implementation is already authorized, proceed within the agreed boundaries; ask before changing architecture or scope beyond that agreement and preserve explicit checkpoints.
- If implementation exposes a missing assumption, revisit that specific decision using the new evidence. Do not infer that every extra parameter, cast, or lock requires a redesign. Propose broader restructuring separately when the demonstrated problem warrants it.

## Decision principles

- Prefer transforming data or configuration at the boundary when the generic engine already supports the required behavior.
- Prefer explicit static data when the domain is finite and known. Do not add runtime generation or configurability without demonstrated variability.
- Keep domain exceptions inside their owning domain. Do not leak them into shared engines, global contexts, or UI orchestration.
- Preserve dependency direction. Domain code may prepare inputs for generic code; generic code should not learn domain concepts.
- Challenge new concepts that cross multiple layers. Require each new public parameter, shared type, adapter, or alternate execution path to justify its maintenance cost.
- Keep UI components focused on interaction and presentation. Move domain policy out when the UI merely forwards or branches on it.
- Protect existing runtime characteristics. A locally computed feature should not acquire a network dependency, and an offline-first flow should remain locally executable.

These are decision criteria, not absolute bans. Change a stable abstraction when the required behavior genuinely belongs there and the broader contract improves as a result.

## Review the solution

Check both the proposal and the final diff:

1. Is the variation primarily data or behavior?
2. Does the change modify a stable abstraction unnecessarily?
3. Are dependencies pointing from the domain toward generic machinery?
4. Is one domain rule repeated or exposed across several layers?
5. Did an intermediate concept appear only to bridge misplaced responsibilities?
6. Could the same outcome be achieved by preparing the correct input at one boundary?
7. Do tests prove behavior while architectural debt remains unexamined?

Recommend the smallest correction that localizes responsibility. Preserve the user's chosen behavior and avoid broad cleanup.

## Integration

When `suri-mode` routes here, apply this review before committing to an architectural approach. Reapply it during final diff review only if boundaries, ownership, or shared contracts changed. Then return control to the active Suri workflow.

Do not invoke `suri-mode` from this skill. Do not create a routing cycle.
