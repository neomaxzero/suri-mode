---
name: principle-build-the-lever
description: Decide whether existing tooling or a small script can reduce repetitive work, mistakes, or verification cost in bulk edits, migrations, and checks. Do not require automation for every non-trivial task.
---

# Build the Lever

Automate when the concrete benefit exceeds the cost of building, checking, and maintaining the tool. Direct execution is valid when it is simpler or the cases require individual judgment.

## Choose the approach

- Look for existing commands, codemods, scripts, and checks before creating another tool.
- Consider repetition, consistency, error risk, and verification effort. A one-off operation can justify a script when that makes it meaningfully safer or easier to verify; task size alone does not require one.
- Keep small or heterogeneous changes direct when a generic transformation would need more complexity than the work warrants. Do not create a file merely to demonstrate that this principle was applied.

## Bound and verify automation

- Establish the intended transformation and explicit targets. Inspect representative cases, including relevant variations, before applying it broadly.
- Validate the transformation on a representative sample and inspect the resulting diff. Use an existing preview or dry-run capability when useful; do not treat matching one sample as proof that every case is covered.
- Apply in coherent, reviewable units under the existing verification and size rules. Verify the actual changed artifacts and behavior where relevant, not just a successful script exit.
- Determine whether rerunning is safe. For non-idempotent transformations, make the input preconditions and stopping behavior clear rather than blindly rerunning against partially transformed data.
- Keep the tool narrow. New dependencies, destructive actions, external mutations, or wider scope still need their existing authorization; automation does not grant it.

## Retain only useful artifacts

- Keep the tool when there is concrete future reuse, reproducibility, or reviewer verification value. Otherwise use the project's temporary-work convention and avoid adding maintenance obligations to the repository.
- Report whether execution was direct, used existing tooling, or used a new script, along with relevant verification. Do not claim time or token savings without supporting evidence.

For work suitable for a deterministic transformation, prefer that over delegating repetitive manual edits. This does not authorize additional agents or require automating judgment-heavy work.
