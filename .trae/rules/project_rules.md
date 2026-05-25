# Trae Rules: Multi-platform Controlled Software Skills v2.3.0

Use these rules for software projects across Web, backend, iOS, Android, mini program, macOS, desktop, Electron, Tauri, Flutter, and React Native.

## Skills

1. `project-indexing`: initialize, rebuild, refresh, or audit graph-aware `docs/ai-index/` indexes.
2. `software-task-creation`: convert user intent into an index-aware controlled task prompt.
3. `controlled-software-task-execution`: execute tasks with pre-execution index checks, impact checks, validation selection, post-task index maintenance checks, and fixed completion summaries.

## Default workflow

1. First run project-indexing to establish, refresh, or audit `docs/ai-index`.
2. Then run software-task-creation to convert user intent into an index-aware task prompt.
3. Finally run controlled-software-task-execution to execute that prompt.
4. During execution: read relevant indexes before source files when indexes exist.
5. Perform a pre-edit impact check before modifying files.
6. Select validation from `TEST_INDEX.md`, `CODE_INTELLIGENCE_INDEX.md`, package scripts, changed files, and docs.
7. After execution, decide whether `docs/ai-index` needs no update, incremental update, or project-indexing refresh / rebuild.
8. Output fixed completion summary.
9. Stop.

## Graph-aware project-indexing rules

Use the project-indexing Index Source Priority during indexing: authority documents, existing AI-readable indexes, optional structured code intelligence, repository files and configuration, then fallback raw search.

Project authority documents always outrank CodeGraph, code graph MCP tools, symbol indexes, AST indexes, call graph data, dependency graph data, route graph data, and test impact graph data.

Structured code intelligence is optional. Do not install CodeGraph, initialize `.codegraph/`, add dependencies, add npm scripts, or modify MCP / agent configuration unless the user explicitly asks in a separate task.

If structured code intelligence is available and fresh, use it to reduce broad grep/read/glob during indexing. If it is unavailable, incomplete, stale, or unable to answer the indexing question, fall back to normal repository scanning and record the fallback reason.

Project-indexing completion summaries must include structured index capability fields: CodeGraph / code graph availability, `.codegraph/`, MCP graph tools, symbol / AST / call graph, dependency graph, test impact graph, index strategy, whether broad grep/read was avoided, and fallback reason.

## Index-aware software-task-creation rules

Generated task prompts must require execution agents to use project authority documents and existing AI indexes before broad source scans. Relevant AI indexes include `PROJECT_INDEX.md`, `TEST_INDEX.md`, `CODE_INTELLIGENCE_INDEX.md`, `INDEX_CHANGELOG.md`, and platform indexes when present.

Task prompts must state allowed files / areas, forbidden files / areas, current stage boundary, forbidden next stage, stop conditions, whether `docs/ai-index` may be modified, whether new files / config / tests / README / USAGE / tasks / examples may be modified, and completion summary requirements.

Task prompts must require a Pre-edit Impact Check covering affected files, modules, entry points, tests, high-risk areas, uncertainty, and whether the impact exceeds the task boundary. Out-of-bound impact must stop execution.

Task prompts must require post-execution index maintenance with exactly one result: `no-index-update-needed`, `incremental-index-update`, or `full-index-refresh-required`.

## Index-aware controlled-software-task-execution rules

Before editing, controlled execution must parse the task prompt and verify task goal, allowed scope, forbidden scope, stop conditions, validation requirements, and completion summary requirements. Missing critical boundaries require stopping.

Before source reads and edits, check `PROJECT_INDEX.md`, `TEST_INDEX.md`, `CODE_INTELLIGENCE_INDEX.md`, and `INDEX_CHANGELOG.md` when present. Missing, stale, incomplete, or conflicting indexes require fallback reason and uncertainty notes.

Authority priority is: user task, project authority documents, AI index, optional structured code intelligence / CodeGraph, repository scan fallback. CodeGraph optional, not required, and never replaces authority documents.

After validation, controlled execution must decide `no-index-update-needed`, `incremental-index-update`, or `full-index-refresh-required`. If refresh is required but not done, do not recommend entering the next step unless the user explicitly allows skipping index refresh.

## High-risk changes require explicit permission

Do not change dependencies, architecture, API contracts, database schema, auth/security, signing, permissions, CI, deployment, production config, Bundle ID, applicationId, appid, entitlements, keystore, certificates, Electron IPC, Tauri permissions, or native platform folders unless explicitly allowed.

## Completion summary

After execution, output:
- 已完成什么，未进入什么
- 主要输出
- 实现内容
- 索引更新
- 验证已通过
- 验证未通过 / 未执行
- 回归验证
- 高风险影响检查
- 说明
- Git 状态
- 是否建议进入下一步
