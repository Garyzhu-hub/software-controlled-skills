# Software Task Creation Template v2.3

使用 `software-task-creation` 将以下需求整理成可交给 Agent 执行的任务 prompt。

正确链路：

```text
project-indexing -> software-task-creation -> controlled-software-task-execution
```

## 原始需求

【填写用户需求】

## 项目类型/平台

- [ ] web-frontend
- [ ] server-backend
- [ ] fullstack
- [ ] ios
- [ ] android
- [ ] miniprogram
- [ ] macos
- [ ] electron
- [ ] tauri
- [ ] flutter
- [ ] react-native
- [ ] 其他：

## 索引策略

- [ ] index-check
- [ ] index-bootstrap
- [ ] index-only-first

## AI index files to read

- [ ] docs/ai-index/PROJECT_INDEX.md
- [ ] docs/ai-index/TEST_INDEX.md
- [ ] docs/ai-index/CODE_INTELLIGENCE_INDEX.md
- [ ] docs/ai-index/INDEX_CHANGELOG.md
- [ ] 平台相关索引：

## Code intelligence index usage

- [ ] entry points
- [ ] key symbols / modules
- [ ] dependency summary
- [ ] critical flows
- [ ] affected tests
- [ ] high-risk areas
- [ ] 不适用 / 不存在

## 阶段边界

当前阶段：

不得进入：

## Allowed files / areas

1.
2.

## Forbidden files / areas

1.
2.

## Pre-edit impact check required

执行 Agent 修改前必须识别：

- affected files：
- affected modules：
- affected entry points：
- affected tests：
- high-risk areas：
- uncertainty：
- 是否超出任务边界：

## Expected affected areas

1.
2.

## Affected tests mapping required

- [ ] 使用 TEST_INDEX.md
- [ ] 使用 CODE_INTELLIGENCE_INDEX.md affected tests mapping
- [ ] 使用 package scripts
- [ ] 使用 changed files
- [ ] 使用 source area -> test mapping
- [ ] 如无法识别，必须说明原因和人工复核项

## 已知限制

1.
2.
3.

## Validation plan

验证选择依据：

1.
2.

## Manual review items

1.
2.

## Post-execution index maintenance required

完成后必须判断：

- [ ] no-index-update-needed
- [ ] incremental-index-update
- [ ] full-index-refresh-required

## Index maintenance expectation

- 是否允许修改 docs/ai-index：
- 是否必须更新 INDEX_CHANGELOG.md：
- 如果需要 refresh / rebuild，是否禁止进入下一步：

## 希望输出

请输出一份 `controlled-software-task-execution` 可直接执行的任务 prompt，必须包含：

1. 当前任务。
2. 任务类型/平台。
3. 任务目标。
4. 阶段边界。
5. 相关索引。
6. 必须读取文件。
7. 允许修改范围。
8. 禁止修改范围。
9. 平台高风险约束。
10. 测试要求。
11. 验证命令。
12. 必须停止条件。
13. 完成后必须按 `Fixed Completion Summary Format` 输出开发完成摘要。
14. AI index files to read。
15. Code intelligence index usage。
16. Pre-edit Impact Check。
17. Affected tests mapping required。
18. Post-execution index maintenance required。
19. Index maintenance expectation。
