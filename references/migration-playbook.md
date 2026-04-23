# Migration Playbook

## Goal

Turn a Claude-oriented skill into a Codex-native skill that installs cleanly, triggers reliably, and can be shared without confusing duplicates.

## Standard Sequence

1. Inspect source layout.
Look for:
- root `SKILL.md`
- `skills/` directory
- helper scripts
- Claude-only instructions
- plugin-only packaging

2. Identify the canonical unit.
Decide whether the repo contains:
- one installable skill folder
- a catalog of many skills
- only guidance, not a real skill

3. Choose a route.
- Direct install: source is already clean and Codex-friendly
- Light adaptation: install first, then improve frontmatter or wording
- Full migration: rewrite packaging and split references

4. Rewrite for Codex if needed.
Focus on:
- clear `name`
- trigger-rich `description`
- concise workflow body
- optional `agents/openai.yaml`
- references only where they reduce noise
- Codex-native priority and safety rules
- removal of Claude-only runtime assumptions

5. Polish installed skills even after direct install.
Look for Claude wording, plugin hooks, marketplace commands, persistent behavior claims, broken examples, and external LLM dependencies.

6. Validate.
Check file structure, BOM, frontmatter, and discovery.

7. Package.
Keep one canonical folder that can be copied into `.codex/skills` or published directly.

## Heuristics

### Direct install is usually enough when

- the repo already has a clear `skills/<name>/SKILL.md`
- the frontmatter is simple
- the description already says what the skill does and when to use it
- the body is operational rather than Claude-marketing-heavy
- the body still makes sense after replacing "Claude" with "Codex" mentally
- helper commands work on the target OS or are clearly marked as external dependencies

Direct install is not complete until the installed skill passes the native polish checklist below.

### Full migration is usually needed when

- there is no usable `SKILL.md`
- the description is too vague to trigger well in Codex
- the file begins with BOM
- the repo depends on Claude-only plugin commands or marketplace behavior
- the repo mixes multiple aliases and duplicate directories
- the body relies on `.claude-plugin` hooks, `SessionStart`, `UserPromptSubmit`, or automatic Claude plugin persistence
- style skills claim they are always active without respecting Codex skill triggering and conversation scope
- scripts call external LLM backends without warning about credentials and data transfer

## Codex-Native Polish Checklist

Run this checklist on every installed or migrated skill before calling it ready.

### Frontmatter

- Use `SKILL.md` with simple YAML frontmatter.
- Keep `name` stable, lowercase, and folder-like.
- Write `description` as a strong one-line trigger string when possible.
- Include realistic user phrasing for Codex, not only Claude slash commands.
- Validate with `scripts/check_skill_md.py`.

### Body

- Replace "Claude should" with "Codex should" when it describes the active agent.
- Keep "Claude", "Anthropic", or "Claude CLI" only when they are real external systems or upstream context.
- Remove install-only marketing, marketplace copy, and duplicated README content.
- Add priority rules for behavior-changing skills: system, developer, safety, and tool instructions win.
- Preserve exact text requirements for code, commands, paths, URLs, quoted errors, tests, and citations.
- Rewrite "active forever" or "every response" claims to respect Codex skill activation and conversation scope.
- Remove broken mojibake and unverified non-ASCII examples.

### Packaging

- Install one canonical skill folder.
- Do not copy `.claude-plugin`, marketplace metadata, or plugin hook folders unless they are useful resources for the Codex skill.
- Keep helper scripts only when they are deterministic or explicitly documented.
- Move long explanations into `references/`; keep `SKILL.md` operational.

### Commands and dependencies

- Use commands that match the target OS. On Windows, prefer `py -3` or explicit executables over bare `python3`.
- If scripts call Anthropic, Claude CLI, OpenAI, or other network services, document required credentials and data boundaries.
- If a script cannot work in Codex without a Claude-only runtime, either rewrite it, mark it external, or remove it from the installed skill.

## Caveman Case Study Rules

From the `JuliusBrussee/caveman` port:

- A clean `skills/<name>/SKILL.md` layout still needed rewrite because descriptions used folded YAML poorly for local trigger scoring.
- A response-style skill needed Codex priority rules so brevity never hides warnings, test results, exact errors, or requested code.
- Claude plugin persistence language had to become Codex conversation-scope activation.
- Unicode examples copied from README were mojibake; removing them was better than shipping broken examples.
- A compression helper used Anthropic/Claude as backend, so the Codex skill had to warn about third-party data transfer instead of pretending compression was local.
- Windows install instructions needed `py -3 -m scripts`, not only `python3`.

## Strong Description Pattern

Use a description that answers both:
- what the skill does
- when it should be used

Good pattern:

`Convert, install, audit, and package Claude Code skills for Codex. Use when the user asks to port a Claude skill to Codex, install a GitHub skill repo, fix discovery, or package a migrated skill for sharing.`

## Packaging Pattern

Prefer this shape:

```text
skill-name/
├── SKILL.md
├── agents/
│   └── openai.yaml
├── references/
│   ├── migration-playbook.md
│   └── discovery-troubleshooting.md
└── scripts/
    ├── inspect_skill_repo.py
    └── check_skill_md.py
```

## Final Rule

If the user asks whether the migration is done, and the skill is not discoverable in the target Codex environment, the answer is still no.

If the skill is discoverable but still contains Claude-only rules that will not work in Codex, the answer is also no.
