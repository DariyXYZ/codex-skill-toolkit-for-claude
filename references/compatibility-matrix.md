# Compatibility Matrix

Use this matrix to choose the route quickly.

## Install recommendation tiers

- `tier_1_direct_install`: safe direct install candidate
- `tier_2_direct_install_with_review`: direct install is likely fine, but review naming, collisions, or dependency signals first
- `tier_3_migrate_after_inspection`: inspect carefully, then migrate or polish before relying on it
- `tier_4_extract_and_migrate`: packaging is too Claude-specific or indirect for raw install
- `tier_5_not_recommended`: treat as docs-only, incompatible, or too risky without source restructuring

## Case: repo contains `skills/<name>/SKILL.md`

Recommended route:
- install that exact folder first
- read the installed `SKILL.md`
- validate discovery
- run Codex-native polish before calling it ready

Risk level:
- low to medium

Migration needed when:
- the description is weak
- the name is misleading
- discovery fails
- the body still assumes Claude plugin lifecycle, hooks, slash-command persistence, or marketplace behavior
- scripts require Claude-only runtime without documenting the dependency

## Case: repo contains `.claude/skills/<name>/SKILL.md`

Recommended route:
- treat the repo as a platform-specific skill source
- inspect `.claude/skills/` child folders directly
- install or migrate the exact child skill folder you need

Risk level:
- medium

Migration needed when:
- the repo only documents Claude marketplace install paths
- there is no obvious Codex-native packaging
- the skill name or description needs cleanup for Codex triggering
- the useful skill logic is wrapped in plugin-only files that Codex will not execute

Extra signals:
- `skill.json`
- `.claude-plugin/plugin.json`
- multi-platform CLI install instructions in `README.md`
- `hooks/`
- `SessionStart`
- `UserPromptSubmit`

## Case: repo contains only a root `README.md` and links to other skills

Recommended route:
- do not install the repo as a skill
- treat it as a catalog
- select concrete downstream skill repos instead

Risk level:
- high for direct install

Migration needed when:
- the user wants a Codex-native curated package derived from that catalog

## Case: repo contains a skill, but instructions are Claude-marketplace-specific

Recommended route:
- inspect the real skill content
- preserve logic, not installation wrapper
- migrate to Codex-native packaging
- remove plugin hooks and marketplace commands from the installed skill unless they are only documented as upstream context

Risk level:
- medium to high

Migration needed when:
- the workflow depends on Claude-only marketplace or plugin behavior
- the skill claims automatic activation via Claude hooks or plugin state

## Case: skill installs but does not appear in `codex debug prompt-input`

Recommended route:
- treat as failure
- inspect BOM, frontmatter, description quality, and installation path

Risk level:
- high

Migration needed when:
- frontmatter or discovery wording is poor

## Case: skill appears in Codex but triggers unreliably

Recommended route:
- strengthen the `description`
- add clearer trigger phrases
- remove vague wording

Risk level:
- medium

Migration needed when:
- the original wording was written for Claude-specific invocation behavior

## Case: skill appears in Codex but still behaves like a Claude plugin

Recommended route:
- treat discovery as necessary but not sufficient
- rewrite `SKILL.md` body for Codex
- remove or quarantine plugin wrappers, hooks, and marketplace assumptions
- add Codex priority rules for style or behavior-changing skills
- document external LLM or CLI dependencies honestly

Risk level:
- medium to high

Migration needed when:
- the skill says it is active every response without user activation or conversation scope
- it depends on `.claude-plugin`, `SessionStart`, `UserPromptSubmit`, or Claude settings files
- command examples are not runnable in the target environment
- it sends file contents to Anthropic, Claude CLI, OpenAI, or another service without warning
