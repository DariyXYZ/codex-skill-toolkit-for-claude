# Install Report

## Input

```text
/plugin marketplace add nextlevelbuilder/ui-ux-pro-max-skill
```

## Install Hint Classification

- Scenario: `claude-plugin-marketplace-add`
- Codex route: `inspect-marketplace-repo-and-extract-skill`
- Extracted values: `{'marketplace_ref': 'nextlevelbuilder/ui-ux-pro-max-skill'}`
- Notes: Claude marketplace syntax usually points to a repo with .claude-plugin metadata, not a Codex-ready skill folder.

## Repository Analysis

- Repo kind: `platform-installer-repo`
- Recommended route: `extract-platform-skill-folder`
- Compatibility score: `70`
- Install tier: `tier_2_direct_install_with_review`
- Candidate count: `7`
- Conflict count: `3`
- Repo notes: Repo contains .claude/skills. Treat it as a platform-specific skill source and install or migrate individual child skill folders.; Root skill.json suggests this repo may support multi-platform installation workflows.; skill.json explicitly lists codex support; check whether the repo ships a Codex-native install path before migrating manually.; One or more candidate skills have the same frontmatter name as already-installed Codex skills. Review for collisions before installing.

## Candidates

### `banner-design`
- Declared name: `ckm:banner-design`
- Compatibility score: `86`
- Trigger quality: `59` (weak)
- Dependency risk: `low`
- Compatibility notes: Namespaced skill name may merit migration polish.
- Best prompt overlap: `create a design system with tokens and components` -> create, design

### `brand`
- Declared name: `ckm:brand`
- Compatibility score: `78`
- Trigger quality: `45` (weak)
- Dependency risk: `medium`
- Compatibility notes: Medium dependency/runtime complexity.; Namespaced skill name may merit migration polish.

### `design`
- Declared name: `ckm:design`
- Compatibility score: `78`
- Trigger quality: `48` (weak)
- Dependency risk: `medium`
- Compatibility notes: Medium dependency/runtime complexity.; Namespaced skill name may merit migration polish.
- Best prompt overlap: `create a design system with tokens and components` -> create, design, tokens

### `design-system`
- Declared name: `ckm:design-system`
- Compatibility score: `50`
- Trigger quality: `78` (good)
- Dependency risk: `high`
- Compatibility notes: High dependency/runtime complexity.; Conflicts with an already installed skill name.; Namespaced skill name may merit migration polish.; Good trigger quality.
- Best prompt overlap: `create a design system with tokens and components` -> design, system, tokens

### `slides`
- Declared name: `ckm:slides`
- Compatibility score: `86`
- Trigger quality: `64` (weak)
- Dependency risk: `low`
- Compatibility notes: Namespaced skill name may merit migration polish.
- Best prompt overlap: `create a design system with tokens and components` -> create, design, tokens

### `ui-styling`
- Declared name: `ckm:ui-styling`
- Compatibility score: `50`
- Trigger quality: `80` (good)
- Dependency risk: `high`
- Compatibility notes: High dependency/runtime complexity.; Conflicts with an already installed skill name.; Namespaced skill name may merit migration polish.; Good trigger quality.
- Best prompt overlap: `create a design system with tokens and components` -> components, create, design

### `ui-ux-pro-max`
- Declared name: `ui-ux-pro-max`
- Compatibility score: `72`
- Trigger quality: `65` (good)
- Dependency risk: `low`
- Compatibility notes: Conflicts with an already installed skill name.; Good trigger quality.
- Best prompt overlap: `build a responsive web interface` -> build, responsive, web
