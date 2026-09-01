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

When native delegation and `gpt-5.6-luna` are available, run one critic with high reasoning. Give it the task, evidence, diff or proposed decision, and verification performed. Ask for contradictions and the smallest corrective action. The critic does not edit files.

Treat the output as a challenge, not authority. Check every accepted finding against the artifact. Keep the review internal unless uncertainty materially affects the user.

If delegation is unavailable, answer the same questions locally. Never use an API key or an external paid model as a fallback.
