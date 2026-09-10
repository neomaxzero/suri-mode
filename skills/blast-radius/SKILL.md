---
name: blast-radius
description: Assess indirect breakage from changes to shared components, contracts, or behavior with downstream effects. Use for targeted impact reviews or when a concrete shared dependency makes the diff alone insufficient; do not audit the whole repository by default.
---

# Blast Radius

Identify what a change could break beyond the edited files, and check the concrete assumptions its safety depends on.

## Trace the relevant effects

- Read the actual diff and distinguish implementation changes from changed behavior or contracts. Follow relevant consumers and dependencies far enough to evaluate a plausible failure path, not every possible repository relationship.
- For shared UI, inspect affected usage patterns, props, styles, lifecycle behavior, and relevant states beyond the first screen tested.
- For backend and infrastructure, consider external consumers, persisted formats, and deployed versions that can coexist when they touch the changed contract. No local search results is not proof of no consumers.
- When behavior depends on a library, inspect the installed version and applicable local changes rather than assuming current documentation describes the shipped implementation.

## Test the safety assumptions

- State the specific assumptions that would make the change safe or unsafe. Avoid forcing all changes into a single safety claim or inventing an exhaustive list of hypothetical risks.
- Check those assumptions with the cheapest adequate evidence: relevant source, existing tests, a focused probe, or the running application. Match the depth to the failure risk and distinguish static reasoning from observed behavior.
- Prefer existing verification paths. A new script, broad test suite, or multiple agents is not required by default; use them only when the unresolved question justifies their cost.
- Do not run production mutations merely to prove a risk. Preserve authorization and diagnostic approval gates. When evidence is unavailable, name the gap instead of presenting the assumption as settled.

## Report a useful review

- Briefly state what changed, which consumers or contracts matter, and the evidence supporting the conclusion.
- Separate confirmed problems, relevant unresolved risks, and concerns checked and cleared. Do not invent numeric probabilities or describe an untested concern as a confirmed failure.
- Explain the concrete failure and consequence, then recommend the smallest next check or correction. For backend, database, or infrastructure decisions, provide enough context and tradeoffs for a frontend-focused developer to judge the proposal.
- A review request authorizes investigation, not fixes. Propose scope expansion separately; never add compatibility solely because a consumer might hypothetically exist.
