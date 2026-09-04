---
name: principle-prove-it-works
description: Define observable success before implementation and verify the actual result before declaring completion. Use when validating task outputs or delegated work; distinguish structural checks, runtime observations, and unverified claims.
---

# Prove It Works

Match each completion claim to direct evidence from the actual result. A proxy, a delegate's summary, or a successful build proves only what it observes.

## Define the check before the change

- State the requested outcome and an observable success criterion before implementation. Identify the input, expected result, and relevant environment or state. Do not replace a failed criterion with an easier one merely to declare success.
- Choose checks proportional to impact and failure risk. Reuse relevant existing checks; include meaningful failure paths or persistence checks when they are part of the requested behavior.
- Stay within authorized scope. Verification can send messages, charge money, or change data. Prefer isolated fixtures or a suitable test environment; obtain approval for consequential external actions. Never treat a request to verify as blanket authorization for production writes.

## Observe the real result

- Confirm that the check targets the current artifact, version, process, environment, and data. Cached screenshots, timestamps, or derived state are insufficient when they can hide the behavior being claimed.
- For executable changes, exercise the actual feature path from input to output. A build establishes buildability, not runtime correctness. For integrations, check the full communication path when safely available; label mocked or partial coverage explicitly.
- For other artifacts, inspect the delivered content and the property being claimed. Valid skill metadata does not establish useful agent behavior; matching uploaded file hashes establishes content equality, not functional quality.
- Inspect delegated artifacts and relevant behavior yourself. A delegate's summary helps locate evidence but does not replace it.
- If a check fails, investigate both the system and the observation method. Do not assume either is wrong. Where practical, use a known failing case or independent observation to check whether the test can detect the relevant defect.

## Make evidence repeatable when useful

Automate checks that are important to repeat, error-prone by hand, or needed for a complex comparison. Prefer existing tools over new scripts. Do not add trivial tests or permanent maintenance solely to produce an evidence artifact.

Keep enough evidence to reproduce consequential findings: the command or steps, target version, relevant conditions, and observed result. Avoid secrets and unnecessary output. Commit evidence only when requested or required by the repository's workflow.

## Report the boundary of proof

State what passed, what failed, and what could not be checked. Link or identify the evidence when useful. Do not claim full completion when a required outcome remains unverified; distinguish implementation complete from verification blocked or partial.

A successful check supports the tested outcome under the observed conditions. It does not automatically prove a root-cause explanation, cover untested conditions, or replace a required human approval.
