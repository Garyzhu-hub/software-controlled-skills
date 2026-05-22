使用 `controlled-software-task-execution` 执行以下任务。

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

验证命令：
```bash
pnpm lint
pnpm typecheck
pnpm --filter @ai-prototype-workbench/mcp-server validate:mcp-tools
pnpm --filter @ai-prototype-workbench/web build
```

完成后必须按 `Fixed Completion Summary Format` 输出开发完成摘要，开头必须明确：
已完成 Stage 10，未进入 Stage 11。
