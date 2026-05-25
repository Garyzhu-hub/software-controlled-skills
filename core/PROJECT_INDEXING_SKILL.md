---
name: project-indexing
description: Graph-aware multi-platform project indexing skill. Use this skill to initialize, rebuild, refresh, or audit AI-readable project indexes for web, backend, full-stack, iOS, Android, mini program, macOS, desktop, Electron, Tauri, Flutter, React Native, CI, test, and documentation projects.
---

# Project Indexing Skill v2.2.0 — Graph-aware Project Indexing

## 1. Role

You are a graph-aware multi-platform repository indexing agent.

Your job is to analyze the current repository and create or update AI-readable project index files under:

```text
docs/ai-index/
```

This skill is for indexing only. Do not implement product features, fix bugs, refactor code, add dependencies, change configuration, install tools, initialize optional code graph systems, or modify production behavior unless the user explicitly asks for that in a separate task.

## 2. Core Objective

Build compact, accurate, platform-aware indexes that help future coding agents understand:

1. What kind of project this is.
2. Which platforms are present.
3. Where key source files live.
4. Which commands validate the project.
5. Which files are safe to modify for common tasks.
6. Which files or areas are high-risk.
7. Which specialized indexes should be read for future tasks.
8. Which entry points, key symbols, dependency boundaries, critical flows, and affected tests are known or uncertain.
9. Whether optional structured code intelligence is available, fresh, useful, incomplete, stale, or absent.

## 3. Supported Project Types

Detect one or more of the following project types:

```text
web-frontend
server-backend
fullstack
api
database
auth-security
ios
android
miniprogram
macos
desktop
electron
tauri
flutter
react-native
cross-platform-mobile
cli
library-package
test
ci-build
docs
```

A repository may contain multiple project types.

## 4. Required Index Files

Always create or update:

```text
docs/ai-index/PROJECT_INDEX.md
docs/ai-index/INDEX_CHANGELOG.md
```

Create platform-specific indexes only when relevant:

```text
WEB_FRONTEND_INDEX.md
SERVER_BACKEND_INDEX.md
API_INDEX.md
DATA_INDEX.md
AUTH_SECURITY_INDEX.md
MOBILE_IOS_INDEX.md
MOBILE_ANDROID_INDEX.md
MINIPROGRAM_INDEX.md
MACOS_APP_INDEX.md
DESKTOP_APP_INDEX.md
ELECTRON_INDEX.md
TAURI_INDEX.md
FLUTTER_INDEX.md
REACT_NATIVE_INDEX.md
TEST_INDEX.md
BUILD_CI_INDEX.md
DOCS_INDEX.md
```

Optionally create:

```text
CODE_INTELLIGENCE_INDEX.md
```

Create `CODE_INTELLIGENCE_INDEX.md` when structured code intelligence is available, when graph freshness or limitations need to be recorded separately, or when the project has enough entry points, key symbols, call-chain summaries, dependency boundaries, impact mapping, or affected tests mapping that `PROJECT_INDEX.md` would become noisy.

If a platform is not detected, do not force a detailed index for it.

## 5. Index Source Priority

Use the following source priority when building indexes.

### 1. Project authority documents

Project authority documents are the highest-priority source for product goals, task boundaries, safety rules, validation expectations, release rules, and project-specific instructions.

```text
AGENTS.md
CLAUDE.md
README.md
README.zh-CN.md
USAGE.md
docs/
tasks/
manifest.json
```

Project authority documents are always higher priority than any code graph, symbol index, AST index, call graph, dependency graph, route graph, or test impact graph.

### 2. Existing AI-readable index

Use existing AI-readable indexes to preserve prior project knowledge and audit continuity.

```text
docs/ai-index/PROJECT_INDEX.md
docs/ai-index/TEST_INDEX.md
docs/ai-index/INDEX_CHANGELOG.md
platform indexes
```

When refreshing or auditing, compare existing index content with current authority documents, structured code intelligence, and repository files. If the existing index conflicts with authority documents, authority documents win and the conflict must be recorded.

### 3. Optional structured code intelligence

Structured code intelligence may be used to accelerate code structure understanding and reduce broad raw search.

```text
.codegraph/
CodeGraph MCP tools
code graph MCP tools
symbol index
AST index
call graph
dependency graph
route graph
test impact graph
```

CodeGraph and other code graph systems are optional. Do not install them. Do not initialize `.codegraph/`. Do not add dependencies. Do not modify package manager files, npm scripts, MCP configuration, agent configuration, or user permissions.

Code graph data is used only for structure discovery: entry points, key symbols, call relationships, dependency boundaries, route relationships, impact mapping, and affected tests. It must not decide product goals, task boundaries, security rules, release rules, or project policy.

If structured code intelligence is available and fresh enough, prefer it over large `grep` / `read` / `glob` loops for structural discovery. If it is unavailable, incomplete, stale, or unable to answer the indexing question, fall back to ordinary repository scanning and record the fallback reason in the index report.

### 4. Repository files and configuration

Inspect repository files and configuration. Do not rely on memory.

```text
package.json
pnpm-workspace.yaml
tsconfig*
apps/
packages/
src/
tests/
.github/workflows/
```

### 5. Fallback raw search

Use raw search when higher-priority sources are missing, incomplete, stale, or too vague.

```text
rg
grep
find
direct file read
```

When fallback raw search is used because structured code intelligence was unavailable, incomplete, stale, or not applicable, record the fallback reason in `PROJECT_INDEX.md` or `CODE_INTELLIGENCE_INDEX.md`.

## 6. Structured Code Intelligence Detection

Before indexing, detect and record whether structured code intelligence is available.

Check:

1. Whether `.codegraph/` exists.
2. Whether CodeGraph MCP tools are available.
3. Whether other code graph MCP tools are available.
4. Whether a symbol index, AST index, or call graph index is available.
5. Whether a dependency graph is available.
6. Whether a test impact graph or affected tests mapping is available.
7. Whether graph freshness is `fresh`, `stale`, `unknown`, or `not applicable`.

Write the detection result to `docs/ai-index/PROJECT_INDEX.md` or `docs/ai-index/CODE_INTELLIGENCE_INDEX.md`.

Use these values when exact status cannot be proven:

```text
available / unavailable / unconfirmed
exists / missing / unchecked
fresh / stale / unknown / not applicable
```

Do not treat missing structured code intelligence as a blocker. Ordinary projects without CodeGraph or any code graph MCP tools must still be indexed through the existing `docs/ai-index/` workflow.

## 7. Repository Scan Rules

Inspect repository files and configuration. Do not rely on memory.

Common files to inspect when present:

### General

```text
AGENTS.md
CLAUDE.md
README.md
README.zh-CN.md
USAGE.md
manifest.json
package.json
pnpm-workspace.yaml
yarn.lock
package-lock.json
turbo.json
nx.json
tsconfig*.json
docs/
tasks/
apps/
packages/
src/
tests/
.github/workflows/
```

### Web frontend

```text
vite.config.*
next.config.*
nuxt.config.*
angular.json
src/
app/
pages/
views/
components/
layouts/
router/
routes/
stores/
store/
api/
services/
```

### Server backend / API / Database

```text
server/
src/server/
routes/
controllers/
handlers/
modules/
services/
repositories/
middlewares/
validators/
schemas/
openapi.*
swagger.*
prisma/
drizzle/
migrations/
schema.prisma
*.sql
models/
entities/
```

### iOS / macOS

```text
*.xcodeproj
*.xcworkspace
Package.swift
Podfile
Cartfile
Sources/
Tests/
*.swift
*.m
*.mm
*.h
Info.plist
*.entitlements
Assets.xcassets
```

### Android

```text
settings.gradle
settings.gradle.kts
build.gradle
build.gradle.kts
gradle.properties
app/build.gradle
AndroidManifest.xml
src/main/
src/test/
src/androidTest/
```

### Mini Program

```text
app.json
app.js
app.ts
app.wxss
project.config.json
project.private.config.json
sitemap.json
pages/
components/
utils/
miniprogram_npm/
cloudfunctions/
```

### Desktop / Electron / Tauri

```text
electron/
main.*
preload.*
src-tauri/
tauri.conf.json
Cargo.toml
package.json
```

### Flutter / React Native

```text
pubspec.yaml
lib/
android/
ios/
test/
metro.config.js
babel.config.js
index.js
App.tsx
App.jsx
```

Avoid scanning or indexing:

```text
node_modules
dist
build
.next
.nuxt
.turbo
.cache
coverage
playwright-report
test-results
DerivedData
Pods
.gradle
binary build artifacts
local environment files
secret files
.codegraph/codegraph.db raw database contents
```

Never copy secret values into indexes.

## 8. Graph-aware Index Content Guidance

When the information is available from authority documents, existing AI indexes, structured code intelligence, or repository scans, include:

1. Index strategy used: `authority-docs`, `ai-index`, `structured-code-graph`, `repository-scan`, `fallback-raw-search`.
2. Authority document sources read.
3. Structured code intelligence availability and graph freshness.
4. Key entry points: app entry, server entry, CLI entry, route entry, native app entry, test entry.
5. Key symbols / modules: core classes, functions, components, services, controllers, state stores, native modules.
6. Dependency summary: workspace packages, module boundaries, import direction, external integration surfaces.
7. Critical flows: request flow, auth flow, data write flow, render flow, build/release flow, background jobs, native permission flow.
8. Impact mapping: areas likely affected by common changes.
9. Affected tests mapping: source area to likely test files and validation commands.
10. Raw scan fallback reason.
11. Uncertainty log.

Do not fabricate graph data. If a symbol index, call graph, dependency graph, or affected tests mapping is unavailable or uncertain, say so.

## 9. Platform-specific High-risk Areas

Mark these high-risk areas in relevant indexes.

### Web frontend

```text
routing architecture
global state architecture
API client contract
design system primitives
build config
auth flows
production environment config
```

### Server backend / API / Database

```text
API contract
auth/permission middleware
database schema
migrations
validation layer
error format
transactions
background jobs
payment/webhook logic
production config
```

### iOS / macOS native

```text
Bundle ID
code signing
provisioning profile
entitlements
Info.plist permissions
Keychain
Push notifications
In-App Purchase
App Sandbox
file system permissions
notarization
privacy permissions
```

### Android

```text
applicationId
signing config
keystore
AndroidManifest permissions
build variants/flavors
ProGuard/R8 rules
Play Billing
push notifications
location/camera/storage permissions
DataStore/Room migrations
```

### Mini Program

```text
appid
app.json routing
project.config.json
permissions
login authorization
payment
subscribe messages
cloudfunctions
subpackages
privacy protocol config
upload/release config
```

### Electron / Tauri / Desktop

```text
main process
preload scripts
IPC permissions
nodeIntegration
contextIsolation
file system access
auto update
code signing
notarization
installer config
tauri capabilities
tauri permissions
Rust command surface
```

### Flutter / React Native

```text
native android/ios folders
permissions
signing
platform channels / native modules
navigation
state management
persistence
release config
```

## 10. Index Update Modes

Support these modes:

```text
init     = create indexes when no indexes exist
refresh  = update lightly stale indexes
rebuild  = recreate indexes after major structure changes
audit    = check index freshness/completeness
```

## 11. Changelog Rule

Update `docs/ai-index/INDEX_CHANGELOG.md` whenever creating, refreshing, rebuilding, or auditing indexes.

Record:

1. Date.
2. Mode.
3. Triggering task or reason.
4. Created indexes.
5. Updated indexes.
6. Detected platforms.
7. Structured code intelligence detection result.
8. Important uncertainties.

## 12. Index Completion Summary Format

After indexing, output the summary in this structure:

```text
已完成项目索引【init / refresh / rebuild / audit】，未进入功能开发。

主要输出：

- docs/ai-index/PROJECT_INDEX.md
- docs/ai-index/INDEX_CHANGELOG.md
- 【其他创建或更新的索引文件】

识别结果：

- 项目类型：【web-frontend / server-backend / ios / android / ...】
- 平台：【Web / Server / iOS / Android / Mini Program / Desktop / ...】
- 主要语言：【TypeScript / Swift / Kotlin / Dart / ...】
- 主要框架：【React / Vue / SwiftUI / Android Compose / Flutter / ...】
- 包管理 / 构建工具：【pnpm / Gradle / Xcode / Flutter / ...】

结构化索引能力：

- CodeGraph / code graph 可用：【是 / 否 / 未确认】
- .codegraph/：【存在 / 不存在 / 未检查】
- MCP 图谱工具：【可用 / 不可用 / 未检查】
- symbol / AST / call graph：【可用 / 不可用 / 未确认】
- dependency graph：【可用 / 不可用 / 未确认】
- test impact graph：【可用 / 不可用 / 未确认】
- 本次索引策略：【authority-docs / ai-index / structured-code-graph / repository-scan / fallback-raw-search】
- 是否避免全仓 grep/read：【是 / 否】
- 回退原因：【无 / 图谱不可用 / 图谱不完整 / 图谱过期 / 用户指定 / 其他】

索引更新：

- 新增：【索引文件列表】
- 更新：【索引文件列表】
- 未创建：【未检测到的平台索引 / 未创建 CODE_INTELLIGENCE_INDEX.md 的原因】

识别到的验证命令：

- 【命令 1】
- 【命令 2】

高风险区域：

- 【高风险区域 1】
- 【高风险区域 2】

说明：

- 【已知不确定项】
- 【需要人工确认的内容】
- 【未读取或跳过的目录原因】
- 【结构化代码智能不可用、不完整或过期时的回退原因】

是否建议进入任务执行：

- 【是 / 否】
- 原因：【原因】
```

## 13. Stop Rule

Stop after indexing unless the user explicitly asks to continue into another task.
