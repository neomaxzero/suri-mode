# Day workflows

Use the smallest route that matches the task. Show progress often enough for the user to steer, but pause only for an important decision.

## Investigation

Use for technical research and questions about code.

1. Define the exact claim or question.
2. Read the implementation and follow the real runtime or data flow.
3. Read relevant tests. Read history only when it can explain intent, regressions, or unusual constraints.
4. Run a focused probe when code reading cannot establish behavior.
5. Separate facts, inferences, alternate explanations, and unknowns internally.
6. Challenge important claims before answering.
7. Return a short conclusion, the strongest evidence, and uncertainty only when material.

Do not edit code in this route unless the user also asks for a change.

## Bug fix

1. Read and follow [Prove the Cause](../skills/principle-prove-the-cause/SKILL.md) for diagnosis, approval gates, correction, and causal verification.
2. Add or extend tests only for important regressions, core user journeys, security, permissions, payments, data loss, or behavior that is otherwise difficult to verify. Tests supplement the causal evidence; passing tests do not establish the diagnosis.

## Feature

1. Understand the current user behavior and nearby conventions.
2. Name the core data shape and boundaries before writing logic.
3. When a relevant decision exists, compare at least two credible options and their debt.
4. Pause for the user only when the decision meets the important-decision threshold.
5. Implement the smallest useful vertical slice.
6. Verify the behavior through the real user surface.
7. Review the diff for avoidable code, concepts, dependencies, and future obligations. Remove what does not earn its place.

## Refactor

1. State the concrete reason and the behavior that must remain unchanged.
2. Capture a useful baseline. It may be observable behavior, branch count, duplication, public surface, performance, or support for an immediate feature.
3. Compare alternatives only when the structural choice is relevant.
4. Make one small structural change at a time.
5. Verify behavior after each meaningful unit.
6. Confirm the result reduced the targeted burden. Do not call movement or renaming an improvement by itself.

## Existing failures

When verification fails for a suspected pre-existing reason, confirm that the failure also occurs before the change when practical. Preserve evidence. Continue only when the current change can be shown not to worsen it.
