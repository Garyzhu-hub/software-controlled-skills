使用 `controlled-software-task-execution` 执行以下任务。

正确链路：
project-indexing -> software-task-creation -> controlled-software-task-execution

索引策略：
index-check

当前任务：
【填写任务名称】

任务类型/平台：
【web-frontend / server-backend / fullstack / ios / android / miniprogram / macos / electron / tauri / flutter / react-native / test / ci-build / docs / bugfix / refactor】

阶段边界：
已完成后不得进入【后续阶段】。

任务目标：
1.
2.
3.

允许修改：
1.
2.

Allowed files / areas：
1.
2.

禁止修改：
1. 不新增依赖。
2. 不修改架构。
3. 不修改 API / 数据库 / 鉴权 / 安全。
4. 不修改 CI / 部署 / 生产配置。
5. 不修改签名、证书、权限、Bundle ID、applicationId、appid。
6. 不修改本任务无关文件。

Forbidden files / areas：
1.
2.

AI index files to read：
1. docs/ai-index/PROJECT_INDEX.md
2. docs/ai-index/TEST_INDEX.md
3. docs/ai-index/CODE_INTELLIGENCE_INDEX.md
4. docs/ai-index/INDEX_CHANGELOG.md

Pre-edit Impact Check：
修改前识别 affected files / affected modules / affected entry points / affected tests / high-risk areas / uncertainty。若超出任务边界，停止并报告。

Affected tests mapping required：
优先参考 TEST_INDEX.md、CODE_INTELLIGENCE_INDEX.md affected tests mapping、package scripts、changed files、source area -> test mapping。

验证命令：
```bash
【按项目实际情况填写】
```

Post-execution index maintenance required：
完成后必须判断 no-index-update-needed / incremental-index-update / full-index-refresh-required，并说明判断依据。

完成后必须按 `Fixed Completion Summary Format` 输出开发完成摘要，明确说明：
已完成【当前任务/阶段】，未进入【后续阶段】。
