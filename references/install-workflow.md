# Install Workflow

This note describes the semi-automatic install workflow layered on top of repo inspection and install-hint classification.

## Goal

Take a user-provided install hint and move from "tutorial syntax" to "Codex action plan" with minimal manual reasoning.

## Inputs

- install hint text
- optional local repo path
- optional chosen candidate folder

## Outputs

- normalized install scenario
- Codex route
- repo compatibility score
- install recommendation tier
- candidate skill shortlist
- Codex-native polish decisions
- optional Markdown report
- optional local copy into `.codex/skills`

## Script roles

### `classify_install_hint.py`

Normalizes tutorial syntax into a Codex route.

### `inspect_skill_repo.py`

Evaluates repo structure, dependency risk, trigger quality, conflicts, and install tier.

### `generate_install_report.py`

Produces a Markdown record of the analysis.

### `install_skill_flow.py`

Combines the previous scripts into a semi-automatic installer flow.

## Recommended usage pattern

1. Classify the install hint.
2. Inspect the repo or local extracted package.
3. Review score, tier, conflicts, and trigger quality.
4. If the path is local and safe, copy the chosen skill into `.codex/skills`.
5. Read the installed `SKILL.md` and run the Codex-native polish checklist from `migration-playbook.md`.
6. Patch the installed skill or source package so instructions are native to Codex.
7. Re-run validation and discovery checks.
8. Generate a report when the result should be reviewed, shared, or committed.

## Native polish gates

Do not call an install complete only because `codex debug prompt-input` sees it. Also check:

- no Claude-only plugin hooks are expected to run
- no marketplace install command remains as the operative Codex instruction
- behavior-changing skills include Codex priority and safety rules
- style skills preserve exact code, command, error, path, URL, and test output
- helper scripts have working commands for the user's OS
- external LLM calls and data transfer are documented
- broken encoding or copied README examples are removed
