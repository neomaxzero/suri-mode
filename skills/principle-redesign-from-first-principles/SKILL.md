---
name: principle-redesign-from-first-principles
description: Compare design alternatives using current requirements only when the user explicitly requests a redesign or explicitly invokes this skill for a design review. Do not activate for bug fixes, small features, or local refactors merely because the current design could be improved.
---

# Redesign From First Principles

Use a fresh-design thought experiment to evaluate an explicitly requested redesign, not to justify rewriting an existing system.

## Respect the entry condition

- Apply only to an explicitly requested redesign or an explicit invocation for design review. A request to fix, improve, clean up, or refactor does not by itself authorize a redesign.
- If a bug or small feature reveals a structural problem, describe the evidence and propose a separately scoped change. Do not switch into redesign or begin that work without approval.
- A request to compare designs authorizes analysis, not implementation. Preserve the user's stated scope and existing compatibility obligations.

## Compare against reality

- Read the affected implementation and relevant callers, contracts, and constraints. Identify which existing assumption conflicts with a confirmed current requirement.
- Ask what structure would fit if that requirement had been known from the start. Use the answer as a comparison, not as a mandatory target.
- Compare keeping or extending the existing design with a bounded redesign. Include migration effort, compatibility, operational risk, maintenance cost, and the cost of reversing the choice.
- Do not justify abstractions, extension points, or scope with hypothetical future requirements. Retaining the current design is a valid conclusion.

## Deliver only the agreed change

Before implementation, obtain approval for any expansion of scope or change to contracts, ownership, compatibility, or other important constraints. If implementation is authorized, deliver the chosen change incrementally, update affected references and documentation, and verify the agreed behavior after each increment. Do not propagate a speculative redesign through unrelated callers.
