---
name: principle-model-the-domain
description: Apply when writing stateful logic, or when code branches extensively or repeats a shape assumption across files. Encode domain rules in a fitting data structure instead of scattered conditionals. Do not force an abstraction onto already clear, local code.
---

# Model the Domain

Encode the real domain in a data structure instead of scattering it across conditionals.

Scattered booleans, repeated shape assumptions, and branching spread across files add accidental complexity. A structure that matches the domain can rule out invalid states and remove duplicated decisions. Choose it while writing the behavior rather than deferring a known mismatch to a future refactor.

## Choose a fitting structure

- A state machine instead of scattered booleans, phases, or lifecycle checks.
- A typed object or model instead of loose parameters or repeated shape assumptions.
- A map, registry, lookup table, or discriminated union instead of branching spread across files.
- A reducer or command/event model instead of ad hoc state mutations.
- A module organized around one body of domain knowledge instead of spreading the same rules across load, validate, transform, and save stages. Execution order alone does not establish ownership.
- A small module boundary that gathers repeated behavior, ownership, or invariants.
- A queue, cache, index, graph, tree, or normalized collection where the data access pattern calls for it.

These are options, not required components. When none fits, identify what the code must never allow and how the data gets read, then choose the structure that encodes those constraints.

## Avoid forced abstractions

Prefer straightforward code when the current shape is already clear, local, and unlikely to grow. Be skeptical of an abstraction that adds indirection without removing branches, duplicated rules, invalid states, or lifecycle risk.

An additional if/else branch or a second boolean that must stay in sync with the first is a signal to inspect the model, not an automatic defect. A simple boolean does not require a state-machine framework.

Keep legitimate load, transform, and save pipelines when they express a real processing flow. Reorganize only when the stages duplicate domain rules or obscure ownership; do not rename or merge stages merely because they follow execution order.
