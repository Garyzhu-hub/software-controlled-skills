# 多平台软件受控 Skill 包 v2.2.0 使用说明

本版在 v2.1 的基础上将 `project-indexing` 升级为 v2.2.0 — Graph-aware Project Indexing。

## 1. 三个 Skill 的分工

```text
project-indexing
= 初始化索引 / 全量重建索引 / 索引审计
= 输出索引完成摘要
= 检测可选 structured code intelligence，并记录 symbol / call graph / dependency graph / affected tests 等结构化信息

software-task-creation
= 把用户想法整理成可执行任务 prompt
= 自动在任务 prompt 中加入“完成后必须输出固定摘要”的要求

controlled-software-task-execution
= 执行任务 / 轻量索引检查 / 任务后增量更新索引
= 输出固定开发完成摘要
```

## 2. 为什么要加固定完成摘要

Codex 在阶段任务完成后输出的摘要非常适合做阶段审计，例如：

```text
已完成 Stage 10，未进入 Stage 11。

主要输出：
实现内容：
验证已通过：
回归验证已通过：
说明：
Git 状态：
是否建议进入下一步：
```

v2.1 已经把这种摘要格式固化进 `controlled-software-task-execution`。

## 3. v2.2.0 — Graph-aware Project Indexing

v2.2.0 只升级 `project-indexing`，不重构 `controlled-software-task-execution` 和 `software-task-creation`。

索引来源优先级：

1. 项目权威文档：`AGENTS.md`、`CLAUDE.md`、`README.md`、`README.zh-CN.md`、`USAGE.md`、`docs/`、`tasks/`、`manifest.json`。
2. 已有 AI-readable index：`docs/ai-index/PROJECT_INDEX.md`、`TEST_INDEX.md`、`INDEX_CHANGELOG.md` 和平台索引。
3. 可选 structured code intelligence：`.codegraph/`、CodeGraph MCP tools、code graph MCP tools、symbol index、AST index、call graph、dependency graph、route graph、test impact graph。
4. 仓库文件和配置：`package.json`、workspace 配置、`tsconfig*`、`apps/`、`packages/`、`src/`、`tests/`、CI 配置。
5. fallback raw search：`rg`、`grep`、`find`、直接读取文件。

项目权威文档永远高于 CodeGraph 或任何代码图谱。代码图谱只用于加速代码结构理解，不用于决定产品目标、任务边界、安全规则、发布规则或项目政策。

本包不会安装 CodeGraph，不会初始化 `.codegraph/`，不会新增依赖，不会新增 npm script，不会修改 MCP / agent 配置，也不会要求所有项目必须生成代码图谱。没有结构化代码索引时，仍然按普通 `docs/ai-index/` 流程完成索引，并在索引报告中记录回退原因。

## 4. 推荐工作流

### 第一次接入项目

```text
使用 project-indexing 初始化当前项目索引。
请识别项目类型和平台，创建 docs/ai-index/ 下的相关索引。
请检测 structured code intelligence 是否可用；如果不可用，请回退到普通仓库扫描并记录原因。
本次只做索引，不做功能开发。
完成后按索引完成摘要格式输出。
```

### 创建任务 prompt

```text
使用 software-task-creation 帮我把以下需求整理成可交给 Agent 执行的任务 prompt：

需求：
...
项目类型：
...
限制：
...

要求：
任务 prompt 必须包含完成后按 Fixed Completion Summary Format 输出摘要。
```

### 执行任务

```text
使用 controlled-software-task-execution 执行以下任务。

索引策略：index-check

当前任务：
...

完成后必须按 Fixed Completion Summary Format 输出开发完成摘要。
```

## 5. 固定开发完成摘要字段

执行任务完成后必须包含：

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

## 6. 安装到 Codex / 通用 .agents

```bash
cd 你的项目根目录
unzip software-controlled-skills-multiplatform-kit-v2_2.zip
cp -R software-controlled-skills-multiplatform-kit-v2_2/.agents ./
cp software-controlled-skills-multiplatform-kit-v2_2/AGENTS.example.md ./AGENTS.md
mkdir -p tasks
cp software-controlled-skills-multiplatform-kit-v2_2/tasks/*.md ./tasks/
```

## 7. 安装到 Claude Code

```bash
cd 你的项目根目录
unzip software-controlled-skills-multiplatform-kit-v2_2.zip
mkdir -p .claude/skills
cp -R software-controlled-skills-multiplatform-kit-v2_2/.claude/skills/* .claude/skills/
```

## 8. 安装到 Trae

```bash
cd 你的项目根目录
unzip software-controlled-skills-multiplatform-kit-v2_2.zip
mkdir -p .trae/rules
cp software-controlled-skills-multiplatform-kit-v2_2/.trae/rules/project_rules.md .trae/rules/project_rules.md
```

## 9. 安装到 Cursor

```bash
cd 你的项目根目录
unzip software-controlled-skills-multiplatform-kit-v2_2.zip
mkdir -p .cursor/rules
cp software-controlled-skills-multiplatform-kit-v2_2/.cursor/rules/*.mdc .cursor/rules/
```
