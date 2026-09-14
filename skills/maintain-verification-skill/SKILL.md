---
name: maintain-verification-skill
description: Update an existing repository verification skill when affected flows, commands, selectors, or prerequisites change, or when the user requests a review. Verify corrected flows without defaulting to a whole-application audit or scheduled maintenance.
---

# Maintain a Verification Skill

Keep an existing verification guide accurate for the affected scope. Distinguish outdated instructions from product regressions.

## Locate and bound the work

- Locate the existing repository verification skill and relevant helpers or flow documentation. If several plausible targets exist and the request does not identify one, ask which to maintain. If none exists, report that and propose creation separately.
- Read the target instructions and establish the affected flows from concrete changes or the user's requested coverage. Do not audit every feature merely because the guide includes a feature map.
- Use existing source, scripts, and tests to identify outdated commands, selectors, routes, or prerequisites. Start locally with relevant evidence; subagents are not required by default.

## Correct the guide, not the product

- Change only the verification skill and resources it owns within the agreed scope. Reuse maintained run commands and stable interaction handles rather than duplicating setup or building a new harness unnecessarily.
- Distinguish instruction drift, a verification-tool limitation, a missing environment prerequisite, and a product defect. If intended behavior is unclear, investigate or ask; do not rewrite expected results merely to match broken behavior.
- Report product defects separately. Maintenance does not authorize fixing product code, adding dependencies, changing infrastructure, or expanding coverage.

## Verify affected flows

- Follow the guide's launch, readiness, isolation, and permission requirements before driving the application. Confirm that the instance is the intended one, and reassess readiness after unexpected behavior.
- Run the modified verification paths and inspect their observable results, including relevant side effects. Source inspection alone does not establish that a corrected command or selector works.
- Expand checks only when a shared helper change, new failure, or unresolved risk affects additional flows. If the user explicitly requests a complete review, account for that full scope and identify coverage gaps.
- Correct and rerun affected guide or helper errors within scope. Do not keep retrying when the evidence indicates an unavailable prerequisite or uncertain external effect.
- Clean up only processes and scratch state created for this work, following the guide. Preserve evidence and user sessions, including after failed attempts.

## Report coverage honestly

- State what was checked, what changed, and which flows were exercised. Separate successful observations, product defects, and blocked or unverified paths.
- Label unexecuted corrections as unverified. Do not claim the entire guide is current from a partial pass or treat missing access as proof that a flow is unreachable for users.
- Do not create branches or PRs, publish, schedule recurring maintenance, or expand into unrelated work without the applicable authorization. If nothing needs correction, leave the files unchanged.
