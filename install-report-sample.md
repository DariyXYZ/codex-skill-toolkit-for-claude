# Install Report

## Input

```text
https://github.com/anthropics/skills/tree/main/skills/frontend-design
```

## Install Hint Classification

- Scenario: `github-repo-or-tree-url`
- Codex route: `inspect-github-repo-and-install-exact-skill-folder`
- Extracted values: `{'github_url': 'https://github.com/anthropics/skills/tree/main/skills/frontend-design'}`
- Notes: A GitHub URL is the cleanest path for Codex: inspect the repo layout, then install or migrate the exact skill folder.

## Repository Analysis

- Repo kind: `multi-skill-repo`
- Recommended route: `install-exact-skill-folder`
- Compatibility score: `80`
- Install tier: `tier_2_direct_install_with_review`
- Candidate count: `17`
- Conflict count: `2`
- Repo notes: Repo contains a skills/ directory. Install a concrete child skill folder, not the whole repo.; One or more candidate skills have the same frontmatter name as already-installed Codex skills. Review for collisions before installing.

## Candidates

### `algorithmic-art`
- Declared name: `algorithmic-art`
- Compatibility score: `92`
- Trigger quality: `65` (good)
- Dependency risk: `low`
- Compatibility notes: Good trigger quality.
- Best prompt overlap: `create a design system with tokens and components` -> create

### `brand-guidelines`
- Declared name: `brand-guidelines`
- Compatibility score: `92`
- Trigger quality: `75` (good)
- Dependency risk: `low`
- Compatibility notes: Good trigger quality.
- Best prompt overlap: `create a design system with tokens and components` -> design

### `canvas-design`
- Declared name: `canvas-design`
- Compatibility score: `95`
- Trigger quality: `96` (strong)
- Dependency risk: `low`
- Compatibility notes: Strong trigger quality.
- Best prompt overlap: `create a design system with tokens and components` -> create, design

### `claude-api`
- Declared name: `claude-api`
- Compatibility score: `92`
- Trigger quality: `65` (good)
- Dependency risk: `low`
- Compatibility notes: Good trigger quality.
- Best prompt overlap: `build a responsive web interface` -> build

### `doc-coauthoring`
- Declared name: `doc-coauthoring`
- Compatibility score: `90`
- Trigger quality: `64` (weak)
- Dependency risk: `low`

### `docx`
- Declared name: `docx`
- Compatibility score: `84`
- Trigger quality: `69` (good)
- Dependency risk: `medium`
- Compatibility notes: Medium dependency/runtime complexity.; Good trigger quality.
- Best prompt overlap: `edit a word document` -> document, edit, word

### `frontend-design`
- Declared name: `frontend-design`
- Compatibility score: `75`
- Trigger quality: `89` (strong)
- Dependency risk: `low`
- Compatibility notes: Conflicts with an already installed skill name.; Strong trigger quality.
- Best prompt overlap: `create a design system with tokens and components` -> components, create, design

### `internal-comms`
- Declared name: `internal-comms`
- Compatibility score: `90`
- Trigger quality: `52` (weak)
- Dependency risk: `low`

### `mcp-builder`
- Declared name: `mcp-builder`
- Compatibility score: `74`
- Trigger quality: `80` (good)
- Dependency risk: `high`
- Compatibility notes: High dependency/runtime complexity.; Good trigger quality.

### `pdf`
- Declared name: `pdf`
- Compatibility score: `82`
- Trigger quality: `45` (weak)
- Dependency risk: `medium`
- Compatibility notes: Medium dependency/runtime complexity.
- Best prompt overlap: `analyze a spreadsheet file` -> file

### `pptx`
- Declared name: `pptx`
- Compatibility score: `82`
- Trigger quality: `48` (weak)
- Dependency risk: `medium`
- Compatibility notes: Medium dependency/runtime complexity.
- Best prompt overlap: `create a presentation deck` -> deck, presentation

### `skill-creator`
- Declared name: `skill-creator`
- Compatibility score: `64`
- Trigger quality: `82` (good)
- Dependency risk: `medium`
- Compatibility notes: Medium dependency/runtime complexity.; Conflicts with an already installed skill name.; Good trigger quality.
- Best prompt overlap: `improve motion performance in this app` -> improve, performance

### `slack-gif-creator`
- Declared name: `slack-gif-creator`
- Compatibility score: `84`
- Trigger quality: `80` (good)
- Dependency risk: `medium`
- Compatibility notes: Medium dependency/runtime complexity.; Good trigger quality.

### `theme-factory`
- Declared name: `theme-factory`
- Compatibility score: `90`
- Trigger quality: `62` (weak)
- Dependency risk: `low`

### `web-artifacts-builder`
- Declared name: `web-artifacts-builder`
- Compatibility score: `84`
- Trigger quality: `75` (good)
- Dependency risk: `medium`
- Compatibility notes: Medium dependency/runtime complexity.; Good trigger quality.
- Best prompt overlap: `build a responsive web interface` -> web

### `webapp-testing`
- Declared name: `webapp-testing`
- Compatibility score: `84`
- Trigger quality: `78` (good)
- Dependency risk: `medium`
- Compatibility notes: Medium dependency/runtime complexity.; Good trigger quality.
- Best prompt overlap: `test a local web application` -> local, web

### `xlsx`
- Declared name: `xlsx`
- Compatibility score: `82`
- Trigger quality: `51` (weak)
- Dependency risk: `medium`
- Compatibility notes: Medium dependency/runtime complexity.
- Best prompt overlap: `edit a word document` -> document, edit, word
