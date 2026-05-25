# CODE_INTELLIGENCE_INDEX.md

Last updated: 2026-05-25

## Structured Index Availability

- CodeGraph / code graph available: no
- `.codegraph/`: missing
- CodeGraph MCP tools: unavailable / unconfirmed
- Other code graph MCP tools: unavailable / unconfirmed
- symbol index: unavailable
- AST index: unavailable
- call graph: unavailable
- dependency graph: unavailable
- route graph: not applicable
- test impact graph / affected tests: unavailable

## Graph Freshness

- Status: not applicable
- Evidence: no `.codegraph/` directory and no structured code intelligence files are present in the repository
- Last known update: not applicable
- Stale / uncertain sections: all graph-derived sections are unavailable and represented by conservative file/module summaries

## Symbol Summary

- Symbol: `project-indexing`
  - Kind: skill / workflow module
  - Location: `core/PROJECT_INDEXING_SKILL.md`
  - Role: creates or refreshes repository AI indexes
  - Related modules: `.agents/skills/project-indexing/`, `.claude/skills/project-indexing/`, `.cursor/rules/project-indexing.mdc`, `.trae/rules/project_rules.md`
  - Confidence: high
- Symbol: `software-task-creation`
  - Kind: skill / workflow module
  - Location: `core/SOFTWARE_TASK_CREATION_SKILL.md`
  - Role: converts user intent into index-aware task prompts
  - Related modules: `.agents/skills/software-task-creation/`, `.claude/skills/software-task-creation/`, `.cursor/rules/software-task-creation.mdc`, `.trae/rules/project_rules.md`, `tasks/TASK_TEMPLATE_TASK_CREATION.md`
  - Confidence: high
- Symbol: `controlled-software-task-execution`
  - Kind: skill / workflow module
  - Location: `core/CONTROLLED_SOFTWARE_TASK_EXECUTION_SKILL.md`
  - Role: executes bounded tasks and performs index-aware checks and maintenance decisions
  - Related modules: `.agents/skills/controlled-software-task-execution/`, `.claude/skills/controlled-software-task-execution/`, `.cursor/rules/controlled-software-task-execution.mdc`, `.trae/rules/project_rules.md`, task templates and examples
  - Confidence: high

## Entry Points

- Entry point: package usage overview
  - Type: documentation
  - Location: `README.md`, `README.zh-CN.md`, `USAGE.md`
  - Downstream symbols / modules: all three skills, tasks, examples
  - Related tests: documentation `rg` validation
- Entry point: canonical skill definitions
  - Type: source of truth
  - Location: `core/`
  - Downstream symbols / modules: `.agents`, `.claude`, `.cursor`, `.trae`
  - Related tests: synchronization `diff -q` checks
- Entry point: task prompt templates
  - Type: user-facing templates
  - Location: `tasks/`
  - Downstream symbols / modules: `software-task-creation`, `controlled-software-task-execution`
  - Related tests: keyword and semantic review
- Entry point: release package metadata
  - Type: metadata
  - Location: `manifest.json`
  - Downstream symbols / modules: release package
  - Related tests: `jq . manifest.json`

## Call-chain Summaries

No executable call graph exists.

Conceptual workflow chain:

```text
project-indexing -> software-task-creation -> controlled-software-task-execution
```

## Dependency Boundaries

- Boundary: canonical skill files
  - Allowed direction: `core/` -> distribution copies
  - Important imports: not applicable
  - Risk: distribution copies can drift from canonical skills
  - Notes: compare `.agents` and `.claude` directly with `core`; compare Cursor after removing frontmatter
- Boundary: product templates vs runtime self-index
  - Allowed direction: `_templates/` ships in distribution packages; runtime `docs/ai-index/*.md` should describe this repository only
  - Important imports: not applicable
  - Risk: shipping runtime self-index files would mislead users about their own target project
  - Notes: release packages should include `docs/ai-index/_templates/` and exclude root runtime index files

## Impact Mapping

- Changed area / symbol: `core/SOFTWARE_TASK_CREATION_SKILL.md`
  - Likely affected modules: `.agents`, `.claude`, `.cursor`, `.trae`, task templates, README / USAGE
  - Likely affected flows: task prompt creation
  - Required validation: synchronization checks, keyword checks, manual review
  - Confidence: high
- Changed area / symbol: `core/CONTROLLED_SOFTWARE_TASK_EXECUTION_SKILL.md`
  - Likely affected modules: `.agents`, `.claude`, `.cursor`, `.trae`, task templates, examples, README / USAGE
  - Likely affected flows: controlled execution and completion summary
  - Required validation: synchronization checks, keyword checks, manual review
  - Confidence: high
- Changed area / symbol: release package contents
  - Likely affected modules: generated `software-controlled-skills-multiplatform-kit-v2_*`
  - Likely affected flows: package installation and distribution
  - Required validation: `unzip -l` checks and generated artifact ignore checks
  - Confidence: high

## Affected Tests Mapping

- Source area: skill files
  - Related files / modules: `core/`, `.agents/`, `.claude`, `.cursor`, `.trae`
  - Affected test files: none
  - Validation command: synchronization `diff -q`; keyword `rg`
  - Confidence: high
  - Manual validation required: yes
  - Notes: instruction semantics require review
- Source area: README / USAGE / manifest
  - Related files / modules: `README.md`, `README.zh-CN.md`, `USAGE.md`, `manifest.json`
  - Affected test files: none
  - Validation command: `jq`, version/workflow `rg`
  - Confidence: high
  - Manual validation required: no
  - Notes: syntax and keyword coverage can be checked mechanically
- Source area: distribution package
  - Related files / modules: `software-controlled-skills-multiplatform-kit-v2_*.zip`
  - Affected test files: none
  - Validation command: `unzip -l`
  - Confidence: high
  - Manual validation required: no
  - Notes: ensure templates included and runtime self-index excluded

## Known Limitations

- No AST, symbol index, call graph, dependency graph, route graph, or test impact graph exists.
- All code-intelligence entries are conservative summaries from repository structure and authority documents.
- This repository is mostly Markdown/JSON; graph concepts map to skill and documentation relationships rather than executable code paths.

## Stale / Uncertain Sections

- Graph freshness is not applicable.
- Affected tests mapping is documentation-validation based, not executable-test based.

## Raw Scan Fallback Reason

- Reason: graph unavailable
- Raw search used: `find`, `rg`, direct file reads
- Files read directly: skill files, README files, USAGE, manifest, tasks, examples, templates
- Follow-up needed: update this index when package structure, validation approach, or release packaging rules change
