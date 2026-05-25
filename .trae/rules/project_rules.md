# Trae Rules: Multi-platform Controlled Software Skills v2.2.0

Use these rules for software projects across Web, backend, iOS, Android, mini program, macOS, desktop, Electron, Tauri, Flutter, and React Native.

## Skills

1. `project-indexing`: initialize, rebuild, refresh, or audit graph-aware `docs/ai-index/` indexes.
2. `software-task-creation`: convert user intent into a controlled task prompt.
3. `controlled-software-task-execution`: execute tasks with lightweight index checks, post-task incremental index updates, and fixed completion summaries.

## Default workflow

1. First project setup: run project-indexing.
2. During project-indexing: read authority documents first, then existing AI indexes, then optional structured code intelligence, then repository files, then fallback raw search.
3. Before coding: read relevant indexes.
4. For each task: generate a task execution template.
5. Execute only within allowed scope.
6. Validate.
7. Incrementally update indexes.
8. Output fixed completion summary.
9. Stop.

## Graph-aware project-indexing rules

Use the project-indexing Index Source Priority during indexing: authority documents, existing AI-readable indexes, optional structured code intelligence, repository files and configuration, then fallback raw search.

Project authority documents always outrank CodeGraph, code graph MCP tools, symbol indexes, AST indexes, call graph data, dependency graph data, route graph data, and test impact graph data.

Structured code intelligence is optional. Do not install CodeGraph, initialize `.codegraph/`, add dependencies, add npm scripts, or modify MCP / agent configuration unless the user explicitly asks in a separate task.

If structured code intelligence is available and fresh, use it to reduce broad grep/read/glob during indexing. If it is unavailable, incomplete, stale, or unable to answer the indexing question, fall back to normal repository scanning and record the fallback reason.

Project-indexing completion summaries must include structured index capability fields: CodeGraph / code graph availability, `.codegraph/`, MCP graph tools, symbol / AST / call graph, dependency graph, test impact graph, index strategy, whether broad grep/read was avoided, and fallback reason.

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
