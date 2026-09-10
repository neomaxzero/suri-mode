---
name: suri-mode
description: Orchestrate non-trivial features, bug fixes, technical research, refactors, and code questions through the smallest suitable workflow, relevant specialist skills, evidence-backed decisions, and proportional verification. Use automatically for substantial code work. Use Sleep Mode only when the user explicitly says "sleep mode".
---

# Suri Mode

Route the task. Keep the change small. Challenge important conclusions. Verify the real outcome.

## Operating contract

- Prefer several fast, focused iterations over one large speculative pass.
- Minimize new code, concepts, dependencies, and compatibility layers.
- Investigate at least two credible options only when a real design decision exists. Compare technical debt, code surface, reversibility, repository fit, and expected impact.
- Investigate ambiguity before asking. Ask with evidence when the answer is a product preference or an important decision that observation cannot settle.
- Pause during normal daytime work only for an important decision.
- Be explicit about uncertainty and environmental limits. Never imply evidence, elapsed work, access, or verification that did not occur.
- Never use an OpenAI API key or direct OpenAI API call. Use only the current Codex subscription, native subagents, local tools, and already-authorized connectors.
- Preserve existing user changes. Investigate and ask only when they overlap the requested work.
- Do not modify this skill from lessons learned. Suggest a narrow update when repeated evidence supports one.

## Route the request

Choose one route before acting. Read only its linked reference.

- Code question or technical research. Read [day workflows](references/day-workflows.md), then use Investigation.
- Reported defect or regression. Read [day workflows](references/day-workflows.md), then use Bug fix.
- New or changed behavior. Read [day workflows](references/day-workflows.md), then use Feature.
- Behavior-preserving structural change. Read [day workflows](references/day-workflows.md), then use Refactor.
- Explicit `sleep mode`. Read [Sleep Mode](references/sleep-mode.md) before changing code. Its interview is mandatory.
- No clear match. Investigate enough to classify the work. Do not invent a broad workflow.

For any code change, also read [verification](references/verification.md). For an important decision or before declaring substantial work complete, read [decision review](references/decision-review.md).

## Important decisions

Pause in daytime mode when a choice:

- changes visible behavior;
- introduces meaningful technical debt or a dependency;
- changes architecture, ownership, public APIs, or core data models;
- expands scope;
- removes compatibility;
- is difficult to reverse;
- relies on a product preference that evidence cannot decide.

Present only:

- Option A.
- Option B, and more only when genuinely distinct.
- Debt and tradeoffs.
- Recommendation.
- One concrete question.

Do not pause for ordinary reversible implementation choices.

## Specialist routing

Use a specialist only when its scope matches. Read its full `SKILL.md` before applying it.

- Changing types, function signatures, or variants. Read [principle-type-system-discipline](skills/principle-type-system-discipline/SKILL.md) to prevent concrete mistakes without project-wide type hardening.
- Changing validation, error handling, or data conversion across trust boundaries. Read [principle-boundary-discipline](skills/principle-boundary-discipline/SKILL.md) to locate guarantees and preserve necessary business and runtime checks.
- Only when the user explicitly requests a redesign or explicitly invokes it for design review, read [principle-redesign-from-first-principles](skills/principle-redesign-from-first-principles/SKILL.md). Do not activate it for bugs, small features, or local refactors; propose any structural scope expansion separately and wait for approval.
- Planning verification or declaring a task complete. Read [principle-prove-it-works](skills/principle-prove-it-works/SKILL.md) to define observable success and match completion claims to direct evidence.
- Debugging or root-cause diagnosis. Read [principle-prove-the-cause](skills/principle-prove-the-cause/SKILL.md); obtain human approval before correction when material uncertainty remains or impact is high.
- Stateful logic, repeated shape assumptions, or domain rules scattered across conditionals. Read [principle-model-the-domain](skills/principle-model-the-domain/SKILL.md) to choose a fitting representation without forcing an abstraction.
- Foundational data shapes, shared-state ownership, or prerequisite sequencing that could become costly to revise. Read [principle-preserve-options](skills/principle-preserve-options/SKILL.md) before building dependent logic.
- Refactoring, sizing a diff, adding an abstraction, or threading a decision through several layers. Use `principle-maintainer-effort` to reduce the future maintenance burden without weakening correctness or legitimate boundaries.
- Architecture choices or reviews that cross layers, change ownership or shared contracts, introduce shared abstractions, or affect stable execution boundaries such as persistence, synchronization, or offline behavior. Use `architecture-fit` before implementation.
- New visually significant interface. Use `frontend-skill`.
- Web application behavior or browser UI changes. Use `playwright` and verify visually.
- Native mobile application behavior or UI changes. Verify through the repository's real Android emulator or iOS simulator workflow. Do not substitute a web rendering when the changed surface ships natively.
- Explicit UI, UX, or accessibility review. Use `web-design-guidelines`.
- Large React or Next.js feature review. Use `react-diff-review-agents`. Large means three or more product areas, several layers, a new data model, several phases or commits, or roughly 500 expected changed lines.

Do not route to `karpathy-guidelines`, `human-gated-implementation`, `image-to-code`, or `install-anti-slop`.

## Model use

- Keep the parent execution model. The user's normal preference is `gpt-5.6-sol` with low reasoning.
- For an important decision and before declaring substantial work complete, use one native Codex subagent on `gpt-5.6-luna` with high reasoning for an independent internal challenge when that model and delegation are available.
- Give the critic the evidence and proposed conclusion. Ask it to find contradictions, unsupported claims, alternate explanations, unnecessary code, and missing verification.
- Do not expose the critic transcript. Incorporate valid corrections into the work.
- If the model or delegation is unavailable, perform the same challenge locally and do not seek an API-backed substitute.

## Progress and replies

During daytime work, provide compact progress at meaningful points:

- Discovery.
- Decision or remaining doubt.
- Next step.

Keep final replies short and conclusive. Lead with the result. Include evidence and uncertainty only where they affect trust or the next decision.

## Git and dependencies

- Daytime mode does not create commits unless asked.
- Sleep Mode may create one local commit per verified unit.
- Never mix unrelated existing changes into a commit.
- Daytime mode asks before adding a dependency.
- Sleep Mode follows the dependency authorization established in its interview. If dependencies were not discussed, add none.
- Never install packages globally. Use the existing package manager and lockfile.
- Never add a package that requires an account, API key, or paid service unless explicitly authorized before the run.