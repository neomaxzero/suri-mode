---
name: principle-preserve-options
description: Evaluate foundational data shapes, state ownership, and prerequisite infrastructure before a change makes them expensive to revise. Use for structural choices or sequencing confirmed multi-step work, not isolated edits with no structural consequence.
---

# Preserve Options

Resolve costly structural uncertainty early. Keep local decisions simple and reversible without building for hypothetical requirements.

## Before committing to a structure

- Name the core data shape and the confirmed behavior it must support. Trace its main reads, writes, and access patterns before writing dependent logic.
- Identify who owns each mutable value and who else can change it. If concurrent writers could interfere, settle ownership or isolation before building on shared state.
- Separate decisions that would require caller changes, data migration, or coordination to reverse from cheap local choices. Investigate the former early; avoid making the latter into architecture.
- When a consequential choice remains uncertain, compare credible alternatives against current requirements and the actual cost of changing course. Use a small probe when observation can resolve the uncertainty.

## Sequence only necessary foundations

- Reuse or simplify the existing base before adding infrastructure. Remove dead weight only when it obstructs the agreed change, not as unrelated cleanup.
- Build a shared prerequisite first only when every subsequent step in the confirmed scope needs it and it can be verified independently. Otherwise introduce it with the first step that needs it.
- Do not add generic frameworks, speculative extension points, or a new test stack merely to prepare for possible future work.
- Capture relevant behavior before changing it. This does not require a new test for every fix or a universal test-first workflow.

## Keep the decision bounded

Choose enough structure to make the next verified increment coherent. Reuse domain-modeling, architecture, and concurrency guidance when available rather than redesigning those methods here. A cheaper future change is a reason for a structure only when the current evidence justifies its maintenance cost.
