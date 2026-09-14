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

### Explain how it works

- For code walkthroughs, trace the relevant entry point through decisions, data changes, and observable output. Read the actual implementation rather than inferring behavior from names. Keep the explanation scoped to the question.
- Investigate and explain directly by default. Delegate only when independent exploration earns its context and coordination cost, following Suri's model policy; do not require a separate explainer agent.
- Lead with the main behavior, then explain only the concepts, source locations, and non-obvious details needed to understand or work on that path. Avoid line-by-line narration and mandatory section templates.
- Distinguish source-backed facts, runtime observations, and remaining inferences. Do not invent historical motivations to explain unusual code.
- For this user's backend, database, or infrastructure questions, provide more context: explain the relevant guarantee, what can fail, and why the distinction matters, using a concrete example when helpful. Keep familiar frontend details concise.
- Keep architectural critique separate and include it when requested. An explanation does not authorize refactoring or expanding into an architecture audit. Use the existing architecture-review workflow for a requested critique instead of automatically launching multiple critics.

### Explain why it was chosen

- Anchor historical rationale questions in the relevant code, then inspect associated commits and PR discussions when available. Code shows mechanics; its current shape alone does not establish the original intent.
- Follow concrete leads or important unresolved questions into available documents, tickets, or other authorized sources. Do not search every evidence category or delegate investigators by default. Stop when the evidence adequately answers the question; state material gaps if it does not.
- Cite the specific source for documented motivations. Label plausible explanations as inferences and explain their basis. Do not retrofit a historical reason from what seems sensible today or adopt the user's suggested reason without checking it.
- Surface relevant contradictions and distinguish the reason recorded at the time from constraints that remain valid now. The latest edit is not necessarily the decision's origin.
- A search with no relevant results means the search found nothing, not that a ticket, discussion, or rationale never existed. Report inaccessible sources or missing history when they limit the conclusion; do not invent access or certainty.
- If the record supports multiple explanations or none, say so briefly. A rationale investigation does not authorize removing the code or changing the decision.

### Teach at the user's pace

- When the user wants to learn, start from their question and demonstrated knowledge. Give the smallest complete explanation first, then add detail where their follow-up needs it. Do not deliberately leave the requested answer incomplete to manufacture another turn.
- Connect what the concept is to how it works in the project, using a concrete example when useful. Explain the mechanism rather than listing symbols. Add historical rationale only when relevant and supported; preserve uncertainty from the investigation.
- Reuse available findings from the how and why guidance. Do not repeat investigation or require both workflows, subagents, or new tool calls for every teaching request.
- Keep familiar frontend material concise and give more context for unfamiliar backend, database, and infrastructure guarantees or tradeoffs. Follow the user's requested depth rather than forcing a lecture.
- Use a diagram or other visual only when it materially clarifies the idea. Choose the smallest useful visual; do not require generated images or a sequence of diagrams.
- Keep teaching conversational, without quizzes, forced recaps, or artificial pause instructions unless requested. Teaching and examples do not authorize code changes or external actions.

## Bug fix

1. Read and follow [Prove the Cause](../skills/principle-prove-the-cause/SKILL.md) for diagnosis, approval gates, correction, and causal verification.
2. Add or extend tests only for important regressions, core user journeys, security, permissions, payments, data loss, or behavior that is otherwise difficult to verify. Tests supplement the causal evidence; passing tests do not establish the diagnosis.
3. When a regression test offers useful protection, express observable behavior using an appropriate existing component or integration test path. Confirm it fails for the intended reason before correction, then passes after the fix. Respect the diagnostic approval gate before changing production behavior.
4. Avoid trivial assertions, tests of internal call sequences, excessive mocks, or new infrastructure that costs more than the protection warrants. If an automated regression test is impractical, use a reproducible behavior check and explain the limitation; do not claim failing-before evidence that was not observed.
5. Preserve assertions for required behavior. Do not weaken them to accommodate an incorrect implementation. Run relevant nearby checks proportionately after correction.

## Feature

1. Understand the current user behavior and nearby conventions.
2. Name the core data shape and boundaries before writing logic.
3. When a relevant decision exists, compare at least two credible options and their debt.
4. Pause for the user only when the decision meets the important-decision threshold.
5. Implement the smallest useful vertical slice.
6. Verify the behavior through the real user surface.
7. Review the diff for avoidable code, concepts, dependencies, and future obligations. Remove what does not earn its place.

### Experience within scope

- Prioritize completing the user's core task clearly and reliably. For libraries or internal APIs, consider the consuming developer's experience as well.
- For affected UI flows, provide clear feedback for actions, waiting, errors, and results. Preserve user input on failure when appropriate; avoid redundant messages that obscure the next action.
- Cover relevant accessibility needs and non-ideal states in the changed flow. Reuse established interface patterns rather than introducing a new visual language.
- Add controls, animation, or prototypes only for a concrete benefit or unresolved question. Keep polish and verification proportional to the requested change; do not turn a small feature into an interface-wide redesign.
- Propose scope reductions or additions when they would improve the outcome, and wait for approval before changing the agreed scope. Experience quality does not override correctness or user decisions.

## Refactor

1. State the concrete reason and the behavior that must remain unchanged.
2. Capture a useful baseline. It may be observable behavior, branch count, duplication, public surface, performance, or support for an immediate feature.
3. Compare alternatives only when the structural choice is relevant.
4. Make one small structural change at a time.
5. Verify behavior after each meaningful unit.
6. Confirm the result reduced the targeted burden. Do not call movement or renaming an improvement by itself.

## Existing failures

When verification fails for a suspected pre-existing reason, confirm that the failure also occurs before the change when practical. Preserve evidence. Continue only when the current change can be shown not to worsen it.
