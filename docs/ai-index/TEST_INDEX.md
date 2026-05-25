# TEST_INDEX.md

Last updated: 2026-05-25

## Test Frameworks

No executable test framework detected.

This repository is a Markdown/JSON skill package. Validation is currently performed with repository audit commands rather than unit, integration, or E2E tests.

## Unit Tests

Not detected.

## Integration Tests

Not detected.

## E2E / UI Tests

Not detected.

## Platform Tests

Not detected.

## Source Area To Test Mapping

| Source area | Related files / modules | Affected test files | Validation command | Confidence | Manual validation required | Notes |
| --- | --- | --- | --- | --- | --- | --- |
| Package metadata | `manifest.json` | none | `jq . manifest.json` | high | no | Ensures valid JSON and visible version metadata. |
| README / USAGE docs | `README.md`, `README.zh-CN.md`, `USAGE.md` | none | `rg -n "2.3.0|Index-aware Task Creation|Controlled Execution|project-indexing.*software-task-creation.*controlled-software-task-execution|CodeGraph optional|not required" README.md README.zh-CN.md USAGE.md manifest.json` | high | no | Ensures version and workflow language is present. |
| Skill 2 / Skill 3 rules | `core/`, `.agents/`, `.claude/`, `.cursor/`, `.trae/` | none | `rg -n "PROJECT_INDEX.md|TEST_INDEX.md|CODE_INTELLIGENCE_INDEX.md|INDEX_CHANGELOG.md|affected tests|impact check|Pre-edit Impact Check|Pre-execution Index Check|Post-execution Index Maintenance|no-index-update-needed|incremental-index-update|full-index-refresh-required|stop conditions|allowed files|forbidden files" core .agents .claude .cursor .trae tasks examples` | high | yes | Manual review still required for semantic consistency. |
| Multi-platform skill synchronization | `core/`, `.agents/`, `.claude/`, `.cursor/` | none | `diff -q` checks between canonical skills and distribution copies | high | no | Cursor files must be compared after removing Cursor frontmatter. |
| Release package contents | `software-controlled-skills-multiplatform-kit-v2_3.zip` | none | `unzip -l software-controlled-skills-multiplatform-kit-v2_3.zip | rg "SOFTWARE_TASK_CREATION|CONTROLLED_SOFTWARE_TASK_EXECUTION|PROJECT_INDEXING|README|manifest|TASK|EXAMPLE|CODE_INTELLIGENCE_INDEX_TEMPLATE"` | high | no | Also verify runtime self-index files are excluded from release packages. |
| Whitespace / patch hygiene | all changed tracked files | none | `git diff --check` | high | no | Use before commit. |

## Affected Tests Notes

- Source area: Markdown skill rules and documentation
- Related files / modules: `core/`, `.agents/`, `.claude/`, `.cursor/`, `.trae/`, `tasks/`, `examples/`, README files, `USAGE.md`, `manifest.json`
- Affected test files: none
- Validation command: `rg`, `jq`, `diff`, `unzip -l`, `git diff --check`
- Confidence: medium
- Manual validation required: yes
- Notes: There are no executable tests. Semantic review of instructions remains important.

## Test Commands

```bash
git diff --check
jq . manifest.json
rg -n "2.3.0|Index-aware Task Creation|Controlled Execution|project-indexing.*software-task-creation.*controlled-software-task-execution|CodeGraph optional|not required" README.md README.zh-CN.md USAGE.md manifest.json
rg -n "PROJECT_INDEX.md|TEST_INDEX.md|CODE_INTELLIGENCE_INDEX.md|INDEX_CHANGELOG.md|affected tests|impact check|Pre-edit Impact Check|Pre-execution Index Check|Post-execution Index Maintenance|no-index-update-needed|incremental-index-update|full-index-refresh-required|stop conditions|allowed files|forbidden files" core .agents .claude .cursor .trae tasks examples
unzip -l software-controlled-skills-multiplatform-kit-v2_3.zip | rg "SOFTWARE_TASK_CREATION|CONTROLLED_SOFTWARE_TASK_EXECUTION|PROJECT_INDEXING|README|manifest|TASK|EXAMPLE|CODE_INTELLIGENCE_INDEX_TEMPLATE"
git status --short
```

## Do Not Weaken

- Do not remove required fixed completion summary fields.
- Do not remove index-aware sections added in v2.3.0.
- Do not remove v2.2 graph-aware project-indexing behavior.
- Do not remove validation commands from task templates without replacement.
- Do not commit generated distribution directories or zip files.
- Do not include repository-specific runtime self-index files in release packages.
