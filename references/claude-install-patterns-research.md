# Claude Install Patterns Research

This note summarizes the most common skill installation patterns seen in current Claude materials and popular public repositories.

## Patterns observed

### 1. Web upload as ZIP

Observed in official Claude help materials:
- create a skill folder
- package it as a ZIP
- upload it in Claude's skills UI

Why it matters for Codex:
- this is the cleanest export path for a custom skill
- a Codex adapter can unzip, inspect, and install or migrate the contained skill folder

### 2. Skills API

Observed in official API docs:
- managed skills can be created and managed through the Skills API
- hosted skills are referenced by `skill_id`

Why it matters for Codex:
- a hosted `skill_id` is not enough for local Codex installation
- the toolkit should recognize this route and ask for source files or an exported package

### 3. Claude plugin marketplace commands

Observed in Claude Code docs and many community repos:
- `/plugin marketplace add owner/repo`
- `/plugin install plugin-name@marketplace-name`
- `/plugin add /path/to/marketplace-or-skill`

Why it matters for Codex:
- these commands often target marketplace or plugin packaging, not a directly installable Codex skill folder
- the toolkit should inspect the underlying repo and extract the real skill folders

### 4. Plain GitHub repo links

Observed broadly in tutorials and community repositories:
- users share a GitHub repo and expect the assistant to know how to install it

Why it matters for Codex:
- this is usually the best raw input for a Codex migration workflow
- the toolkit should inspect repo layout and choose the exact child skill folder

## Product implication

The toolkit should not assume all tutorials describe the same install route.
Instead it should:

1. classify the install hint
2. map it to a Codex-compatible route
3. inspect the underlying filesystem skill package
4. decide install tier and migration effort
