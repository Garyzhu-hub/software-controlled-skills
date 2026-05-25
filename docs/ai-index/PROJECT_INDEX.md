# PROJECT_INDEX.md

Last updated: 2026-05-25

## Repository Summary

This repository is the `software-controlled-skills-multiplatform-kit`, a Markdown/JSON skill package for controlled software development workflows across Codex-style agents, Claude Code, Cursor, and Trae.

The package contains three coordinated skills:

1. `project-indexing`
2. `software-task-creation`
3. `controlled-software-task-execution`

Current package version: `2.3.0`.

Version title: `v2.3.0 — Index-aware Task Creation & Controlled Execution`.

## Index Strategy

- Mode: init
- Sources used:
  - authority-docs: yes
  - ai-index: no existing runtime index; templates only
  - structured-code-graph: no
  - repository-scan: yes
  - fallback-raw-search: yes
- Whether broad grep/read was avoided: no
- Raw scan fallback reason: runtime AI indexes were missing; no structured code intelligence was available

## Authority Document Sources

- AGENTS.md: project agent rules and task execution constraints
- CLAUDE.md: not present
- README.md: package overview, version notes, installation pointers
- README.zh-CN.md: Chinese overview, workflow, install instructions
- USAGE.md: detailed Chinese usage workflow
- docs/: index templates under `docs/ai-index/_templates/`
- tasks/: task prompt templates
- manifest.json: package metadata and version history
- Authority conflicts or overrides: none found

## Structured Code Intelligence Availability

- CodeGraph / code graph available: no
- `.codegraph/`: missing
- MCP graph tools: unavailable / unconfirmed
- symbol / AST / call graph: unavailable
- dependency graph: unavailable
- route graph: not applicable
- test impact graph / affected tests: unavailable
- graph freshness: not applicable
- limitations: repository is a documentation/skill package, so graph-like knowledge is derived from file structure and skill relationships, not AST or call graph analysis

## Detected Project Types

- docs
- library-package
- ci-build: not detected
- test: documentation validation only; no executable test framework detected

## Detected Platforms

- Generic `.agents` / Codex-compatible skills
- Claude Code skills
- Cursor rule files
- Trae project rules

No web, server, mobile, desktop, Electron, Tauri, Flutter, React Native, database, or auth runtime project was detected.

## Main Apps / Packages / Modules

- `core/`: canonical skill definitions
- `.agents/skills/`: generic agent / Codex-compatible skill copies
- `.claude/skills/`: Claude Code skill copies
- `.cursor/rules/`: Cursor rule adapters
- `.trae/rules/`: Trae aggregate project rules
- `tasks/`: task prompt templates
- `examples/`: stage/task summary examples
- `docs/ai-index/_templates/`: product index templates shipped to users
- `README.md`, `README.zh-CN.md`, `USAGE.md`: user-facing documentation
- `manifest.json`: package metadata

## Languages and Frameworks

- Markdown
- JSON

No application framework was detected.

## Package / Dependency Managers

- No `package.json`
- No lockfile
- No dependency manager required

## Build / Test / Validation Commands

Use repository-local validation and release-audit commands:

```bash
git diff --check
jq . manifest.json
rg -n "2.3.0|Index-aware Task Creation|Controlled Execution|project-indexing.*software-task-creation.*controlled-software-task-execution|CodeGraph optional|not required" README.md README.zh-CN.md USAGE.md manifest.json
rg -n "PROJECT_INDEX.md|TEST_INDEX.md|CODE_INTELLIGENCE_INDEX.md|INDEX_CHANGELOG.md|affected tests|impact check|Pre-edit Impact Check|Pre-execution Index Check|Post-execution Index Maintenance|no-index-update-needed|incremental-index-update|full-index-refresh-required|stop conditions|allowed files|forbidden files" core .agents .claude .cursor .trae tasks examples
unzip -l software-controlled-skills-multiplatform-kit-v2_3.zip | rg "SOFTWARE_TASK_CREATION|CONTROLLED_SOFTWARE_TASK_EXECUTION|PROJECT_INDEXING|README|manifest|TASK|EXAMPLE|CODE_INTELLIGENCE_INDEX_TEMPLATE"
git status --short
```

## Important Project Rules

- Use `project-indexing` for first-time project indexing, full rebuild, refresh, or audit.
- Use `software-task-creation` to convert user intent into controlled task prompts.
- Use `controlled-software-task-execution` for implementation, bugfix, test, CI, docs, refactor, and audit tasks.
- Do not add dependencies unless explicitly allowed.
- Do not modify architecture, API contracts, database schema, auth/security, signing, permissions, CI, deployment, or production config unless explicitly allowed.
- Do not weaken lint, typecheck, build, test, CI, or release checks.
- Complete only the current task and stop after the completion report.
- Distribution directories and zip files are generated artifacts and must not be committed.

## Source Directories

- `core/`
- `.agents/skills/`
- `.claude/skills/`
- `.cursor/rules/`
- `.trae/rules/`
- `tasks/`
- `examples/`
- `docs/ai-index/_templates/`
- `assets/`

## Generated / Output Directories to Avoid

- `software-controlled-skills-multiplatform-kit-v2_*/`
- `software-controlled-skills-multiplatform-kit-v2_*.zip`
- `.DS_Store`
- editor temporary files
- `.git/`

## Key Entry Points

- Package overview: `README.md`, `README.zh-CN.md`
- Detailed usage: `USAGE.md`
- Agent rules: `AGENTS.md`, `AGENTS.example.md`
- Canonical Skill 1: `core/PROJECT_INDEXING_SKILL.md`
- Canonical Skill 2: `core/SOFTWARE_TASK_CREATION_SKILL.md`
- Canonical Skill 3: `core/CONTROLLED_SOFTWARE_TASK_EXECUTION_SKILL.md`
- Package metadata: `manifest.json`
- Task templates: `tasks/TASK_TEMPLATE_TASK_CREATION.md`, `tasks/TASK_TEMPLATE_MULTIPLATFORM.md`, `tasks/TASK_TEMPLATE_MINI.md`
- Example: `examples/TASK_EXAMPLE_STAGE_SUMMARY.md`

## Key Symbols / Modules

- `project-indexing`
  - Kind: skill
  - Location: `core/PROJECT_INDEXING_SKILL.md`
  - Role: creates, refreshes, rebuilds, or audits `docs/ai-index`
  - Confidence: high
- `software-task-creation`
  - Kind: skill
  - Location: `core/SOFTWARE_TASK_CREATION_SKILL.md`
  - Role: converts user intent into index-aware task prompts
  - Confidence: high
- `controlled-software-task-execution`
  - Kind: skill
  - Location: `core/CONTROLLED_SOFTWARE_TASK_EXECUTION_SKILL.md`
  - Role: executes bounded tasks with index checks, impact checks, validation selection, and post-execution index maintenance
  - Confidence: high

## Dependency Summary

- `core/` is canonical for the three skills.
- `.agents/skills/` and `.claude/skills/` should match their corresponding `core/` files.
- `.cursor/rules/` wraps skill contents with Cursor-specific frontmatter.
- `.trae/rules/project_rules.md` is an aggregate rule summary, not a full copy of each core skill.
- `tasks/` and `examples/` demonstrate the intended workflow.
- `docs/ai-index/_templates/` are product assets and should be included in release packages.
- Runtime self-index files under `docs/ai-index/*.md` describe this repository only and should not be included in release packages.

## Critical Flows

- Indexing flow:
  - `project-indexing` creates or refreshes `docs/ai-index`.
  - Future tasks read `PROJECT_INDEX.md` plus relevant indexes before source scans.
- Task creation flow:
  - `software-task-creation` turns user intent into an index-aware task prompt.
  - Task prompt must include index files to read, allowed/forbidden areas, impact check, validation plan, and index maintenance expectation.
- Task execution flow:
  - `controlled-software-task-execution` parses the prompt, reads indexes, checks impact, validates, checks index maintenance, and outputs the fixed summary.
- Distribution flow:
  - Generate `software-controlled-skills-multiplatform-kit-v2_X/`.
  - Generate `software-controlled-skills-multiplatform-kit-v2_X.zip`.
  - Include product templates under `docs/ai-index/_templates/`.
  - Exclude repository-specific runtime index files under `docs/ai-index/*.md`.

## High-risk Areas

- `core/*_SKILL.md`: canonical skill behavior
- `.agents/skills/*/SKILL.md`: generic distribution copies
- `.claude/skills/*/SKILL.md`: Claude distribution copies
- `.cursor/rules/*.mdc`: Cursor adapters
- `.trae/rules/project_rules.md`: aggregate rules
- `tasks/*.md`: task prompt templates
- `examples/*.md`: workflow examples
- `README.md`, `README.zh-CN.md`, `USAGE.md`: user-facing documentation
- `manifest.json`: package version and metadata
- `docs/ai-index/_templates/`: product templates
- `.gitignore`: controls generated distribution artifacts

## Available Sub-indexes and When to Read Them

- `DOCS_INDEX.md`: read for documentation, README, USAGE, templates, examples, and release packaging tasks.
- `TEST_INDEX.md`: read for validation command selection and source area to validation mapping.
- `CODE_INTELLIGENCE_INDEX.md`: read for structured-code-intelligence availability and file/module impact notes.
- `INDEX_CHANGELOG.md`: read to understand index freshness and last self-index updates.

## Raw Scan Fallback Reason

No prior runtime index existed. Raw repository inspection was required to initialize this index.

## Uncertainty Log

- Uncertainty: no executable test framework detected.
  - Reason: repository contains documentation, skill files, templates, and examples, but no package manager or test runner config.
  - How to verify: inspect future package config if added.
- Uncertainty: no structured code intelligence available.
  - Reason: no `.codegraph/` directory or code graph MCP state in the repository.
  - How to verify: inspect future `.codegraph/` or MCP tooling if explicitly added.

## Known Uncertainties

- Runtime self-index files are useful for this repository, but release packages should contain only `_templates/`, not these repository-specific self-index files.
