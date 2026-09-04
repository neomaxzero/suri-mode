# Proportional verification

Read [Prove It Works](../skills/principle-prove-it-works/SKILL.md) before implementation to define success, then apply it before declaring completion. It owns the general evidence standard; the sections below cover specific verification surfaces.

## Every change

- Inspect the final diff for unrelated changes and unnecessary code.

## Web features and UI

- Run relevant static checks and existing tests.
- Drive the application with Playwright.
- Verify the changed journey as a user.
- Visually inspect every UI change, including small ones.
- Check browser console and relevant network errors.
- Capture visual evidence when it helps comparison or review.

## Native mobile features and UI

- Run relevant static checks and existing tests.
- Build and install the application with the repository's existing Android emulator or iOS simulator workflow.
- Exercise the changed journey on the native target that ships to users.
- Visually inspect every UI change and capture evidence from the emulator or simulator.
- Check native application logs for relevant runtime errors.
- Do not use a web fixture as final visual evidence for a native mobile surface. A web fixture may only support diagnosis and must be labeled as such.

## Bugs

- Reproduce before the fix when possible.
- For UI bugs reported with screenshots, identify and reproduce the exact visible surface before editing. Anchor distinctive content and values from the report to the responsible source code instead of inferring the component from the symptom alone.
- Keep the component, state, data, viewport, and shipping platform consistent between before and after evidence. A nearby surface that exercises similar logic does not verify the reported UI.
- Preserve evidence of the failure.
- Repeat the same reproduction after the fix.
- Check nearby regression paths.

## Refactors

- Establish behavior before and after.
- Run relevant existing tests.
- Compare the structural measure tied to the stated objective.
- Check for unintended visible behavior changes.

## Tests

Create or extend tests only when the behavior is important enough to justify maintenance. Strong candidates include:

- a regression that already occurred;
- a core business or user journey;
- authentication, permissions, payments, security, or data loss;
- behavior that is difficult or unreliable to verify manually;
- logic with broad impact across users or paths.

Prefer integration tests and observable behavior. Do not add trivial tests or chase coverage percentages without user value.
