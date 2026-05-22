# 多平台软件受控 Skill 包 v2.1 使用说明

本版在 v2.0 的基础上增加了强制完成摘要格式。

## 1. 三个 Skill 的分工

```text
project-indexing
= 初始化索引 / 全量重建索引 / 索引审计
= 输出索引完成摘要

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

## 3. 推荐工作流

### 第一次接入项目

```text
使用 project-indexing 初始化当前项目索引。
请识别项目类型和平台，创建 docs/ai-index/ 下的相关索引。
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

## 4. 固定开发完成摘要字段

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

## 5. 安装到 Codex / 通用 .agents

```bash
cd 你的项目根目录
unzip software-controlled-skills-multiplatform-kit-v2_1.zip
cp -R software-controlled-skills-multiplatform-kit-v2_1/.agents ./
cp software-controlled-skills-multiplatform-kit-v2_1/AGENTS.example.md ./AGENTS.md
mkdir -p tasks
cp software-controlled-skills-multiplatform-kit-v2_1/tasks/*.md ./tasks/
```

## 6. 安装到 Claude Code

```bash
cd 你的项目根目录
unzip software-controlled-skills-multiplatform-kit-v2_1.zip
mkdir -p .claude/skills
cp -R software-controlled-skills-multiplatform-kit-v2_1/.claude/skills/* .claude/skills/
```

## 7. 安装到 Trae

```bash
cd 你的项目根目录
unzip software-controlled-skills-multiplatform-kit-v2_1.zip
mkdir -p .trae/rules
cp software-controlled-skills-multiplatform-kit-v2_1/.trae/rules/project_rules.md .trae/rules/project_rules.md
```

## 8. 安装到 Cursor

```bash
cd 你的项目根目录
unzip software-controlled-skills-multiplatform-kit-v2_1.zip
mkdir -p .cursor/rules
cp software-controlled-skills-multiplatform-kit-v2_1/.cursor/rules/*.mdc .cursor/rules/
```
