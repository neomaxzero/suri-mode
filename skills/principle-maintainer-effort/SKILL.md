---
name: principle-maintainer-effort
description: Reduce future maintenance effort when refactoring, sizing a diff, adding abstractions, or threading a decision through several layers. Use when the smallest correct solution may be obscured by wrappers, duplicated choices, or indirect data flow.
---

# Maintainer Effort

Choose the correct solution that leaves the least code and coordination burden for the next maintainer.

## Evaluate the change

- State the observable result before choosing a structure.
- Look for deletion, consolidation, or reuse before adding a new path.
- Trace where each affected decision is made and consumed.
- Treat a path through three or more layers as a review signal, not an automatic failure.
- When a value must cross several layers, check whether the decision belongs closer to its consumer.
- Keep one source of truth for each decision. Represent it with the simplest type that preserves the domain accurately.
- Prefer the smallest diff that solves the full problem. Do not trade away correctness, clarity, or required behavior to reduce line count.

## Preserve useful structure

Do not flatten boundaries that isolate external systems, ownership, security, persistence, or genuinely reusable behavior. A rich interface that hides substantial work can be simpler to maintain than exposing its internals.

## Review before finishing

Remove avoidable pass-through wrappers, duplicated decisions, temporary compatibility paths, and representation leaks introduced by the change. Confirm that a future maintainer can locate the decision and understand its path without reconstructing unrelated layers.
