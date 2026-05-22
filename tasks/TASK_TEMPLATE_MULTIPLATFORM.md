# Multi-platform Controlled Task Template v2.1

使用 `controlled-software-task-execution` 执行以下任务。

## 1. 索引策略

- [ ] index-check：日常默认。只做轻量索引健康检查。
- [ ] index-bootstrap：索引缺失时允许先创建必要索引。
- [ ] index-only-first：先运行 project-indexing，本次不开发。

## 2. 当前任务

任务名称：

任务类型：
- [ ] web-frontend
- [ ] server-backend
- [ ] fullstack
- [ ] api
- [ ] database
- [ ] auth-security
- [ ] ios
- [ ] android
- [ ] miniprogram
- [ ] macos
- [ ] desktop
- [ ] electron
- [ ] tauri
- [ ] flutter
- [ ] react-native
- [ ] cross-platform-mobile
- [ ] cli
- [ ] library-package
- [ ] test
- [ ] ci-build
- [ ] docs
- [ ] bugfix
- [ ] refactor
- [ ] audit

## 3. 任务目标

1.
2.
3.

## 4. 本任务不包括

1.
2.
3.

## 5. 阶段边界

当前阶段：

不得进入的后续阶段：

完成后必须明确说明：

```text
已完成【当前阶段】，未进入【后续阶段】。
```

## 6. 相关索引

请先读取：

1. docs/ai-index/PROJECT_INDEX.md
2.
3.

## 7. 必须先读取的源码/文档

1.
2.
3.

## 8. 允许修改范围

1.
2.
3.

## 9. 禁止修改范围

1.
2.
3.

## 10. 平台高风险约束

默认不允许修改：

1. 依赖。
2. 架构。
3. API contract。
4. 数据库 schema / migration。
5. 鉴权 / 权限 / secrets。
6. CI / 部署 / 生产配置。
7. 签名 / 证书 / provisioning / keystore。
8. Bundle ID / applicationId / appid。
9. Entitlements / Manifest 权限 / 小程序权限。
10. Electron/Tauri IPC / native file access / updater / signing。
11. Flutter / React Native native platform folders，除非明确允许。

明确允许的高风险变更：

1.
2.

## 11. 测试要求

- [ ] 不需要新增测试
- [ ] 需要新增 / 修改单元测试
- [ ] 需要新增 / 修改组件测试
- [ ] 需要新增 / 修改集成测试
- [ ] 需要新增 / 修改 E2E/UI 测试
- [ ] 需要新增 / 修改平台测试，例如 XCTest / Android instrumentation / Flutter test

## 12. 验证命令

```bash
# 按项目实际情况填写
pnpm lint
pnpm typecheck
pnpm test
pnpm build
```

## 13. 必须停止并回报的情况

1. 需要修改禁止范围内的文件。
2. 需要新增未允许的依赖。
3. 需要修改未允许的 API / 数据库 / 鉴权 / 安全 / 签名 / 权限 / CI / 部署。
4. 索引严重过期，需要重建。
5. 验证命令失败且无法判断是否由本任务引起。
6. 需要大范围重构才能完成。

## 14. 完成后输出

完成后必须按 `controlled-software-task-execution` Skill 中的 `Fixed Completion Summary Format` 输出开发完成摘要。

摘要必须包含：

1. 已完成什么，未进入什么。
2. 主要输出。
3. 实现内容。
4. 索引更新。
5. 验证已通过。
6. 验证未通过 / 未执行。
7. 回归验证。
8. 高风险影响检查。
9. 说明。
10. Git 状态。
11. 是否建议进入下一步。
