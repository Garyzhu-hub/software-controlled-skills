# AGENTS.md

## Project Agent Rules

1. Use `project-indexing` for first-time project indexing, full rebuild, or index audit.
2. Use `software-task-creation` when converting a user request into an executable task prompt.
3. Use `controlled-software-task-execution` for implementation, bugfix, test, CI, docs, refactor, and audit tasks.
4. Before task execution, check `docs/ai-index/` and read task-relevant indexes.
5. Do not full re-index on every task. Use lightweight index health checks.
6. After task execution, incrementally update relevant indexes and `INDEX_CHANGELOG.md` when files change.
7. Do not add dependencies unless explicitly allowed.
8. Do not modify architecture, API contracts, database schema, auth/security, signing, permissions, CI, deployment, or production config unless explicitly allowed.
9. Do not modify platform identity files such as Bundle ID, applicationId, appid, signing config, entitlements, keystore, provisioning, or certificates unless explicitly allowed.
10. Do not weaken lint, typecheck, build, test, CI, or release checks.
11. Stop and report when the task becomes high-risk or conflicts with indexes/project rules.
12. Complete only the current task and stop after the completion report.
13. After any execution task, output the fixed completion summary required by `controlled-software-task-execution`.
