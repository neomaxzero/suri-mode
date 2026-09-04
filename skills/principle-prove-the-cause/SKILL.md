---
name: principle-prove-the-cause
description: Investigate defects by distinguishing causal evidence from plausible explanations before proposing a fix. Use for debugging and root-cause diagnosis; require human approval before correction when material uncertainty remains or impact is high.
---

# Prove the Cause

Treat a proposed cause as a hypothesis until evidence distinguishes it from credible alternatives. Confidence, reviewer agreement, and human approval are not causal evidence.

## Investigate without destroying evidence

- Record the observed symptom, expected behavior, conditions, and relevant version or state. Reproduce safely when possible. If reproduction is unavailable, state that limit and use logs, traces, or source evidence without claiming a verified reproduction.
- Preserve relevant failing state before interventions. Use isolated copies or fixtures where possible. Do not delete user data or clear persistent state without authorization. Keep diagnostic instrumentation scoped and avoid logging secrets.
- Trace the mechanism from the suspected cause to the symptom. Identify credible alternative explanations and what observation would distinguish them. Do not invent alternatives merely to fill a quota.
- Prefer a reversible probe that changes one relevant condition while keeping others stable. Check whether the failure follows the predicted condition; repeat or reverse the probe when safe and useful. A passing run alone does not establish causality, especially for intermittent failures.
- When observations do not distinguish the hypotheses, gather targeted evidence rather than applying speculative fixes. Record contradictions and unresolved alternatives, not only supporting evidence.

## Decide whether correction may proceed

A diagnosis is sufficiently supported when the mechanism explains the observed failure, relevant evidence tests its predictions, and no credible unresolved alternative would materially change the proposed correction. Absolute certainty is not required; unsupported confidence is insufficient.

- For a supported diagnosis with low impact, proceed with the smallest correction only when implementation is within the user's request.
- If material uncertainty remains OR impact is high, present the diagnosis and obtain explicit human approval before correction. High impact includes risk to user data, payments, permissions, security, migrations, or difficult-to-reverse changes. Safe, authorized investigation can continue before this gate.
- Present only the observed symptom, proposed cause, supporting evidence, alternatives tested, remaining unknowns, and the minimal change with its risk and verification plan.
- Approval authorizes only the stated action. It does not establish the hypothesis as fact. Label an uncertain intervention as an experiment or mitigation, preserve its uncertainty, and define rollback and a distinguishing check. If no safe bounded intervention is available, report the blocker instead of guessing.
- For high-impact diagnoses, use an independent reviewer when native delegation is available and authorized. Ask for refutations and missing evidence before presenting the diagnosis for approval. Reviewer agreement never substitutes for evidence or human approval.

## Correct the demonstrated mechanism

- Keep legitimate boundary validation and null checks. Reject guards that only hide an unexplained failure, not all defensive checks. A long comment is not proof that code is wrong.
- Search for related instances, but confirm the same mechanism and authorized scope before changing them. Similar-looking code alone does not justify a broad repair.
- Repeat the original failing conditions and relevant nearby behavior after correction. Report precisely what was observed and what remains unverified. Remove unnecessary diagnostic changes without discarding useful evidence.

## Failures after restart

Inspect persisted state, configuration, caches, locks, and initialization order alongside other credible causes. Recovery after clearing a cache is a clue, not proof. Use preserved state to distinguish invalid data, faulty writes, migration errors, timing, and validation failures before choosing a repair.
