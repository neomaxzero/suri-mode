# Suri Mode

A Codex skill that organizes substantial technical work into small, verifiable changes suited to the task and repository.

## What it does

- Selects a workflow for investigations, bug fixes, features, or refactors.
- Asks for human decisions when product behavior, architecture, or scope would change.
- Uses specialist skills only when they add value.
- Verifies outcomes through the real user experience.
- Includes a local `sleep mode` that runs only when explicitly requested.

## Installation

```bash
git clone https://github.com/neomaxzero/suri-mode.git ~/.codex/skills/suri-mode
```

Restart Codex after installation if the skill does not appear.

## Usage

Codex can select this skill automatically for substantial technical tasks. You can also invoke it directly:

```text
$suri-mode investigate this bug and propose the smallest change that fixes it
```

`sleep mode` requires that exact phrase and a short interview to agree on the objective and limits before changing code.

## Structure

```text
suri-mode/
├── SKILL.md
├── agents/openai.yaml
├── references/       # Workflows and verification guidance
└── skills/           # Specialist skills
```

## License

MIT
