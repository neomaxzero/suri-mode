# Sleep Mode

Sleep Mode is an explicitly requested local autonomous run. The exact trigger is `sleep mode`. Do not infer it from ordinary requests for persistence.

## Mandatory interview

Ask as many focused questions as needed before changing code. Close every material ambiguity about:

- the primary objective;
- the measurable success condition;
- current baseline and target;
- scope and exclusions;
- core user or business outcome;
- important design preferences;
- allowed local actions;
- dependency policy for this run;
- verification surface;
- acceptable technical debt;
- related work allowed after the primary objective;
- stopping conditions and known environmental limits.

Summarize the resulting contract and obtain explicit confirmation. Do not begin the autonomous phase before confirmation.

## Local-only boundary

Sleep Mode may:

- inspect and modify local files;
- create or extend high-value tests;
- create local branches;
- create one local commit per verified unit;
- run local checks and applications;
- use native Codex subagents;
- perform related work within the confirmed scope when it has a measurable positive technical or commercial impact.

Sleep Mode may not:

- open or modify pull requests;
- respond to pull request comments;
- send external messages;
- publish, deploy, or merge;
- change production or remote data;
- delete material data;
- purchase or subscribe to services;
- alter secrets;
- use an OpenAI API key or any separately billed model API.

## Execution loop

Read [Sequence Verifiable Units](../skills/principle-sequence-verifiable-units/SKILL.md) before planning units. Enforce its autonomous size limits on local commits and planned delivery groups; this does not authorize opening PRs.

1. Record the baseline and success predicate.
2. Work in small, independently verifiable units.
3. Verify each unit before continuing.
4. Commit each accepted unit locally without unrelated user changes.
5. Measure the result against the baseline.
6. Revert an experiment that does not improve its agreed measure and is not required for the primary objective.
7. After the primary objective, seek related work only inside the agreed scope and only when it has a predeclared or defensible measurable outcome.
8. Stop when no useful measurable work remains, even if eight hours have not elapsed.

Good additional-work priorities are root-cause corrections, less code or branching, fewer dependencies, faster execution, fewer errors, fewer user steps, stronger core-journey reliability, or a business metric already available in the local evidence.

Do not claim that cleanliness or architecture improved without a measure. Useful measures may include lines or branches removed, duplicated paths removed, public surface reduced, execution time, error count, user steps, critical scenarios covered, or an agreed product metric.

## Dependencies

Follow the interview's explicit dependency policy. When the interview did not authorize new dependencies, add none. Never install globally. Use the existing package manager and lockfile. Do not use packages requiring accounts, secrets, API keys, or paid services unless the user authorized that exact dependency before execution.

## Blocked work

- Leave the repository valid and recoverable.
- Record the blocker and evidence.
- Continue with independent measurable work inside scope.
- Stop early when no useful unblocked work remains.

## Final report

Keep it concise:

- Result reached.
- Metrics before and after.
- Local commits created.
- Attempts discarded or reverted.
- Risks and remaining work.
- Steps for the user to verify.
- Actual elapsed work and any interruption or environment limit. Never imply eight hours elapsed when they did not.
