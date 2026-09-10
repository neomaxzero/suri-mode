# Decision review

Use this review internally for important decisions and before declaring substantial work complete.

## Challenge the conclusion

- What evidence would contradict the conclusion?
- Is any inference presented as a fact?
- Is there another reasonable explanation?
- Was real behavior observed, or only inferred from code and tests?
- Does the proposed solution add avoidable code, state, layers, dependencies, or future migration work?
- Does a smaller reversible option produce the same result?
- What relevant verification is still missing?

## Independent critic

Routine completion does not require a separate critic. When material uncertainty or high impact makes an independent challenge useful, follow the token-efficient model policy in [Suri Mode](../SKILL.md). Start with a lightweight model and low reasoning; increase depth only when the specific question requires it. Give the critic the bounded question, relevant evidence, diff or proposed decision, and verification performed. Ask for concise contradictions and the smallest corrective action. The critic does not edit files.

Treat the output as a challenge, not authority. Check every accepted finding against the artifact. Keep the review internal unless uncertainty materially affects the user.

If delegation is unavailable, answer the same questions locally. Never use an API key or an external paid model as a fallback.
