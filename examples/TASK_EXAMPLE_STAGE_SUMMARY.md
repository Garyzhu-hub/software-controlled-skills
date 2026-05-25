使用 `controlled-software-task-execution` 执行以下任务。

正确链路：
project-indexing -> software-task-creation -> controlled-software-task-execution

索引策略：index-check

当前任务：
Stage 10：实现 MCP Server MVP 工具。

任务类型/平台：
server-backend / api / test

阶段边界：
当前只允许完成 Stage 10。
不得进入 Stage 11。

任务目标：
1. 实现 Stage 10 要求的 MVP MCP 工具。
2. 不实现 get_screenshot。
3. 不提供 write_file / run_shell / exec_command 等禁止工具。
4. 补充 validate:mcp-tools 验证覆盖。
5. 输出 Stage 10 审计文档。

允许修改：
1. packages/mcp-server/
2. docs/STAGE_10_AUDIT.md
3. 与 MCP 工具验证直接相关的测试文件。

禁止修改：
1. 不修改 DSL 协议。
2. 不修改组件注册中心。
3. 不修改 Patch 协议。
4. 不修改 Codegen 逻辑。
5. 不实现 get_screenshot。
6. 不新增越权工具。
7. 不进入 Stage 11。

AI index files to read：
1. docs/ai-index/PROJECT_INDEX.md
2. docs/ai-index/TEST_INDEX.md
3. docs/ai-index/CODE_INTELLIGENCE_INDEX.md，如存在
4. docs/ai-index/INDEX_CHANGELOG.md，如存在

Pre-edit Impact Check：
修改前识别 affected files、affected modules、affected entry points、affected tests、high-risk areas 和 uncertainty。如果影响面超出 Stage 10，必须停止并报告。

Affected tests mapping required：
优先参考 TEST_INDEX.md；如存在 CODE_INTELLIGENCE_INDEX.md，参考 affected tests mapping；否则使用 package scripts、changed files 和 source area -> test mapping。

验证命令：
```bash
pnpm lint
pnpm typecheck
pnpm --filter @ai-prototype-workbench/mcp-server validate:mcp-tools
pnpm --filter @ai-prototype-workbench/web build
```

Post-execution index maintenance required：
完成后必须判断 no-index-update-needed / incremental-index-update / full-index-refresh-required。本示例预期为 incremental-index-update：Stage 10 新增 MCP server 工具和验证命令时，应更新相关 docs/ai-index 项和 INDEX_CHANGELOG.md；如果索引缺失或无法安全判断，则标记 full-index-refresh-required。

完成后必须按 `Fixed Completion Summary Format` 输出开发完成摘要，开头必须明确：
已完成 Stage 10，未进入 Stage 11。

摘要中还应包含：

索引使用情况：
- PROJECT_INDEX.md：已使用 / 不存在
- TEST_INDEX.md：已使用 / 不存在
- CODE_INTELLIGENCE_INDEX.md：已使用 / 不存在
- INDEX_CHANGELOG.md：已使用 / 不存在
- 是否回退到源码扫描：是 / 否
- 回退原因：
- 不确定项：

影响面检查：
- affected files：
- affected modules：
- affected entry points：
- affected tests：
- high-risk areas：
- 是否超出任务边界：否
- 处理方式：

索引维护：
- 是否需要更新索引：是
- 判断结果：incremental-index-update / full-index-refresh-required
- 判断依据：
- 已更新索引文件：
- 未更新索引文件：
- INDEX_CHANGELOG.md 是否已更新：
- 是否需要执行 project-indexing refresh / rebuild：
- 是否因索引未更新而禁止进入下一步：
