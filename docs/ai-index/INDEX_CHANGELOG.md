# INDEX_CHANGELOG.md

## 2026-05-25

- Mode: init
- Triggering task: v2.3.0 self-index refresh + release packaging audit
- Created index files:
  - `docs/ai-index/PROJECT_INDEX.md`
  - `docs/ai-index/TEST_INDEX.md`
  - `docs/ai-index/CODE_INTELLIGENCE_INDEX.md`
  - `docs/ai-index/INDEX_CHANGELOG.md`
- Updated index files:
  - None
- Detected platforms:
  - Generic `.agents` skills
  - Claude skills
  - Cursor rules
  - Trae rules
- Structured code intelligence:
  - `.codegraph/`: not present
  - CodeGraph / code graph MCP tools: not confirmed in this repository
  - Symbol / AST / call graph index: not available
  - Dependency graph: not available
  - Test impact graph: not available
  - Graph freshness: not applicable
- Packaging decision:
  - Include `docs/ai-index/_templates/` in release packages.
  - Exclude this repository's runtime index files from release packages:
    - `docs/ai-index/PROJECT_INDEX.md`
    - `docs/ai-index/TEST_INDEX.md`
    - `docs/ai-index/CODE_INTELLIGENCE_INDEX.md`
    - `docs/ai-index/INDEX_CHANGELOG.md`
- Repository decision:
  - Runtime index files are useful for this repository's own controlled workflow and should be committed to this repository.
- Uncertainty:
  - No executable test framework is defined for the repository.
  - No structured code intelligence index is available beyond the authored AI-readable index files.
