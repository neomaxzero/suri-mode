---
name: principle-type-system-discipline
description: Use compiler checks to prevent concrete invalid states, argument confusion, and unhandled variants when changing types or function signatures. Do not turn bugs or small features into project-wide type hardening, branding, or code-generation migrations.
---

# Type System Discipline

Use the language's type system to prevent relevant mistakes in the current change. Strengthen representations only when the safety gained justifies the added complexity.

## Represent the cases callers must handle

- Use variants with associated data when optional fields permit contradictory combinations. Keep a simpler representation when it already expresses the required behavior accurately.
- Prefer constructions that encode real invariants, but check what they actually guarantee. A start plus a duration does not prevent negative durations without an appropriate constraint or validated constructor.
- Consider semantic wrappers or branded identifiers when confusing values of the same primitive type is a concrete risk. Do not wrap every primitive merely for precision.
- For closed sets of variants, use the language's exhaustiveness checking so missing cases become visible when the set changes. Preserve intentional handling of unknown external values rather than pretending an open protocol is closed.

## Preserve the boundary of static guarantees

- Runtime data is not validated by declaring or casting its type. Follow the project's boundary validation approach and preserve business checks, authorization, and state-dependent guarantees.
- Prefer narrowing, validated construction, or a corrected model over assertions that merely silence the compiler. When a conversion is necessary for an integration or a limitation of the type system, keep it localized and justify the invariant that makes it safe.
- A null check or runtime assertion is a review signal, not proof that a type is defective. Keep checks for genuinely optional data or conditions the compiler cannot establish.
- Define behavior for legitimate absence, failure, and empty inputs. Do not force stronger input types when the operation already handles those cases correctly.

## Reuse existing sources of truth

Reuse authoritative types and the repository's existing schema or generation workflow where suitable. Avoid parallel definitions that can drift. Do not add generators, packages, or change public contracts without the required approval.

## TypeScript specifics

- Prefer `unknown` over `any` for data whose shape is not established. Narrow or validate it at the appropriate boundary before use; do not turn this into a repository-wide replacement of existing types.
- Use `satisfies` when the goal is to check that an expression conforms to a type without asserting a conversion. It is a compile-time check, not runtime validation. Keep necessary casts localized and justified under the static-guarantee rules above.
- A user-defined type guard must actually establish the predicate it declares. Check the relevant properties rather than trusting the guard's name or return annotation.
- Derive types with existing declarations and utilities such as `Pick`, `Omit`, or `ReturnType` when that preserves domain meaning and avoids drift. Keep an explicit domain type when derivation would couple unrelated contracts or obscure intent.
- Use an argument object when positional arguments create a concrete ordering or meaning ambiguity. Preserve clear existing signatures rather than converting every function mechanically.

## Verify the bounded change

Run the relevant compiler or type checks and exercise affected runtime behavior when applicable. For a claimed static guarantee, verify that the compiler rejects a representative invalid use when practical. Compilation does not prove external data is valid or the business outcome is correct.

Limit edits to the types, signatures, variants, and necessary callers involved in the agreed task. Do not use this principle to expand a local fix into a type-system redesign.
