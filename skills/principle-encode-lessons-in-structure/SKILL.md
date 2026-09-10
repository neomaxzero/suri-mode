---
name: principle-encode-lessons-in-structure
description: Evaluate evidence of recurring errors or an important preventable failure and propose a minimal durable control. Use when a concrete pattern may justify a type, check, lint rule, or script; do not generalize every correction.
---

# Encode Lessons in Structure

Use demonstrated failures to choose a proportionate preventive mechanism. A repeated instruction is a signal to investigate, not a mandate to automate.

## Establish the evidence

- Consult relevant entries in the repository's `.codex/lessons.md`, following the Repository lessons policy in [Suri Mode](../../SKILL.md). Use available code, history, tests, and user corrections to check their claims. Do not assume memory across sessions without records.
- Distinguish independent occurrences from duplicate descriptions of one event. Similar symptoms may have different causes. Two similar incidents warrant investigation, not an automatic generalization.
- A single confirmed high-impact failure can justify prevention when its risk and mechanism are concrete. Preserve diagnostic uncertainty and human approval gates before correction.

## Choose the smallest effective control

- Prefer existing types, validation, checks, or scripts when they can prevent the demonstrated mistake. Choose by effectiveness and maintenance cost, not a fixed hierarchy of stronger mechanisms.
- Automate objectively checkable rules. Keep contextual decisions with human or agent judgment instead of inventing brittle lint rules.
- Verify that a proposed control catches the actual failure and allows relevant valid cases. Do not claim prevention from a structural check alone.
- Keep improvements inside the authorized task. Propose dependencies, broad refactors, and other scope expansions separately. Do not automatically modify skills or global instructions from a lesson.
- Remove duplicated prose only if the mechanism actually covers its purpose; preserve explanations of intent and exceptions that still matter.

When a control is adopted and verified, update the related repository lesson with its evidence and status. Recording an issue alone does not mean it is fixed. Do not create a backlog item or new abstraction for every observation.
