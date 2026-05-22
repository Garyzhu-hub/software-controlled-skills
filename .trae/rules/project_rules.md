# Trae Rules: Multi-platform Controlled Software Skills v2.1

Use these rules for software projects across Web, backend, iOS, Android, mini program, macOS, desktop, Electron, Tauri, Flutter, and React Native.

## Skills

1. `project-indexing`: initialize, rebuild, refresh, or audit `docs/ai-index/`.
2. `software-task-creation`: convert user intent into a controlled task prompt.
3. `controlled-software-task-execution`: execute tasks with lightweight index checks, post-task incremental index updates, and fixed completion summaries.

## Default workflow

1. First project setup: run project-indexing.
2. Before coding: read relevant indexes.
3. For each task: generate a task execution template.
4. Execute only within allowed scope.
5. Validate.
6. Incrementally update indexes.
7. Output fixed completion summary.
8. Stop.

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
