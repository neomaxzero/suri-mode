---
name: create-verification-skill
description: Create a repository-specific verification skill for a concrete recurring need to launch an app, exercise an important user flow, and capture evidence. Reuse existing verification assets; do not generate a full application map by default.
---

# Create a Verification Skill

Capture how to obtain meaningful evidence in this repository so later sessions can repeat the check without rediscovering the setup. Start with one important flow.

## Establish the scope

- Inspect existing verification skills, scripts, tests, and run documentation first. Extend a suitable existing guide rather than creating a competing source of truth.
- Establish the repository, intended surface, and recurring verification need. Do not create a skill merely because a project lacks one. Ask only when a missing choice changes the intended flow or acceptance criteria.
- Find the real launch command, readiness signal, test data, authentication prerequisites, and existing interaction tools. Do not infer permission to install dependencies, mutate external systems, or change product code from permission to document verification.
- If the environment fails, report the specific obstacle and distinguish unrelated product problems from errors in the generated instructions. Do not automatically repair unrelated startup failures.

## Write a small repository-local skill

- Follow the repository's existing skill location and conventions. For Codex, use `.agents/skills/verify-<app>/SKILL.md` when no project-specific convention exists. Use available skill-authoring guidance for metadata and validation.
- Include only verified commands and necessary prerequisites. Refer to maintained scripts or documentation instead of copying large instructions. Never embed credentials, personal data, or invented selectors.
- Document launch and readiness, how to identify the intended instance, the actions for one important flow, observable expected results, evidence locations, and cleanup. Mark any unexecuted step explicitly as unverified.
- Verify through the real user boundary with available tools. Use the appropriate surface: browser, native app, CLI, or API. Capture relevant effects such as persistence as well as visible feedback. Distinguish a mocked or dry-run check from real integration evidence.
- Keep the flow isolated from user sessions and production data. If isolation or authorization is unclear, resolve that prerequisite before driving a state-changing flow.
- Describe how to stop only processes the verification started and remove only its identified scratch state. Preserve evidence after cleanup.
- Add helpers or supporting files only when they offer concrete reuse or simplify safe verification. Do not generate a full feature catalog, fixed number of scenarios, or new harness by default.

## Validate and hand off

- Run the documented flow end to end when prerequisites and permissions allow: launch, confirm the target instance, perform the actions, inspect results, capture evidence, and clean up.
- Check that the evidence remains available after cleanup. Correct instruction or helper errors within scope and rerun the affected steps; do not turn product regressions into new expected results.
- If the flow cannot run, deliver clearly labeled draft instructions with the blocker and unverified portions. Structural validation alone does not establish that the guide works.
- Report the skill location, flow covered, evidence, and remaining prerequisites. Do not publish, schedule maintenance, or expand coverage automatically.
