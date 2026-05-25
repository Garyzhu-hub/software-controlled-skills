# Software Controlled Skills

[中文说明](README.zh-CN.md)

Multi-platform software development skill kit for controlled task creation, project indexing, and task execution.

This repository contains the v2.2.0 skill package for Codex-style agents, Claude Code, Trae, and Cursor. The package focuses on keeping software work auditable by requiring project indexes, bounded task prompts, and fixed completion summaries after execution.

![Software Controlled Skills guide](assets/software-controlled-skills-guide.png)

## Contents

- `core/`: canonical skill definitions.
- `.agents/skills/`: generic agent / Codex-compatible skill layout.
- `.claude/skills/`: Claude Code skill layout.
- `.cursor/rules/`: Cursor rule files.
- `.trae/rules/`: Trae project rules.
- `tasks/`: task prompt templates.
- `examples/`: example stage completion summary.
- `docs/ai-index/_templates/`: project index templates for common platforms.
- `USAGE.md`: detailed Chinese usage guide.
- `manifest.json`: package metadata.

## Skills

The package includes three coordinated skills:

- `project-indexing`: initialize, rebuild, and audit graph-aware AI-readable project indexes.
- `software-task-creation`: convert rough requirements into executable task prompts.
- `controlled-software-task-execution`: execute bounded software tasks, update indexes, and report fixed completion summaries.

## Quick Start

For generic agent or Codex-style usage, copy the `.agents` directory and `AGENTS.md` into the target project:

```bash
cp -R .agents /path/to/project/
cp AGENTS.md /path/to/project/
cp -R tasks /path/to/project/
```

For Claude Code, copy `.claude/skills` into the target project. For Cursor, copy `.cursor/rules`. For Trae, copy `.trae/rules/project_rules.md`.

See `USAGE.md` for the full workflow and example prompts.

## Graph-aware Project Indexing

v2.2.0 upgrades only `project-indexing`. It can record optional structured code intelligence such as CodeGraph, code graph MCP tools, symbol indexes, call graph data, dependency graph data, route graph data, and affected tests mapping when those sources already exist.

CodeGraph is not a dependency of this package. The skill does not install CodeGraph, initialize `.codegraph/`, add package dependencies, add npm scripts, modify MCP configuration, or require every project to use a code graph. Project authority documents such as `AGENTS.md`, `CLAUDE.md`, `README.md`, `docs/`, `tasks/`, and `manifest.json` remain the source of truth for goals, boundaries, safety rules, and release rules.

When structured code intelligence is unavailable, incomplete, stale, or unable to answer an indexing question, `project-indexing` falls back to the normal `docs/ai-index/` repository scan flow and records the fallback reason.

## Version

Current package version: `2.2.0`.

### v2.2.0 — Graph-aware Project Indexing

- Upgrades `project-indexing` with index source priority and structured code intelligence detection.
- Adds graph-aware project index fields for entry points, key symbols, dependency summary, critical flows, fallback reasons, and uncertainty logs.
- Expands test indexing with source area to affected tests mapping.
- Adds optional `CODE_INTELLIGENCE_INDEX_TEMPLATE.md`.
- Keeps CodeGraph and code graph MCP tools optional, local, and non-authoritative.

Main v2.1 changes:

- Adds fixed completion summary requirements.
- Adds index completion summary requirements.
- Updates task templates with stage boundaries and summary fields.

## License

MIT. See `LICENSE`.
