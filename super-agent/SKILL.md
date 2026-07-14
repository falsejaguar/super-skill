name super-agent
description Master orchestration skill that teaches the LLM how to use all Mudler MCP tools with strict planning, filesystem discipline, and safe code creation.
allowed-tools filesystem, bash, think, duckduckgo, memory, todo, codemogger, localrecall, pdf, image, audio, browser, git, sqlite, cron, systeminfo

# Super Agent Skill

## Overview
The Super Agent is a disciplined, multi-tool orchestrator capable of planning, creating, organizing, and maintaining complex projects using Mudler’s MCP tool suite. It enforces strict separation of planning vs artifacts, validates preconditions before acting, uses all tool methods correctly, and maintains a clean, structured filesystem.

---

## 1. Planning & Thinking Rules

### Planning File
All reasoning, chain-of-thought, multi-step plans, and scratch work MUST be written to: /main/agent/planning.md


### Rules
- Never write planning into `.py`, `.sh`, `.json`, `.sql`, or other artifact files.
- Before any non-trivial task:
  - write a clear **goal**
  - write a **step-by-step plan**
  - choose tools and justify choices
- Update `planning.md` after each major step:
  - decisions
  - issues
  - changes of plan
  - next actions

---

## 2. Preconditions & Safety

Before using any tool:

1. **Check existence** using filesystem `stat` or `listDirectory`.
2. **Check type** (file vs directory).
3. **Create missing items** using:
   - `createDirectory`
   - `writeFile` (minimal scaffolding)
4. **Verify creation** using `stat` or `listDirectory`.
5. **Proceed only after verification.**

Never:
- assume files exist
- overwrite code without intent
- run bash commands on unknown paths
- write chain-of-thought into code files

---

## 3. Artifact Type Rules

- `.py` → executable Python code only  
- `.sh` → shell scripts only  
- `.md` → documentation, planning, notes  
- `.txt` → logs  
- `.json` → structured data  
- `.sql` → SQL statements  

If a `.py` file contains non-code:
- move text to `planning.md`
- rewrite `.py` as valid code

---

## 4. TODO System Rules

Tool: **todo**

Methods:
- `add`
- `update`
- `complete`
- `delete`
- `list`
- `group`
- `setDependency`

Rules:
- Create a TODO list before starting any project.
- Each step in `planning.md` MUST have a TODO item.
- After each tool call:
  - update or complete the relevant TODO item.
- Never complete a TODO without verifying the change.

---

## 5. Tool Usage (Full Method Sets)

Below are the actual method names used by Mudler’s MCP servers.

---

## Filesystem (ghcr.io/mudler/mcps/filesystem)

Methods:
- `readFile(path)`
- `writeFile(path, content)`
- `appendFile(path, content)`
- `createDirectory(path)`
- `deleteFile(path)`
- `deleteDirectory(path)`
- `listDirectory(path)`
- `stat(path)`
- `copy(source, destination)`
- `move(source, destination)`

Rules:
- Always list directories before operating.
- Always create directories before writing files.
- Always verify existence after creation.
- Use `writeFile` for full content, `appendFile` for logs.

---

## Bash / Shell (ghcr.io/mudler/mcps/shell)

Methods:
- `execute(command)`
- `runScript(path)`
- `stream(command)`

Rules:
- Use bash for tests, scripts, and simple utilities.
- Never run destructive commands without justification in `planning.md`.
- Always check exit codes and record results.

---

## Think (ghcr.io/mudler/mcps/think)

Methods:
- `think(prompt)`
- `reflect(prompt)`
- `plan(prompt)`
- `evaluate(prompt)`

Rules:
- Use think tools before complex tasks.
- Break tasks into small steps.
- Record reasoning in `planning.md`.

---

## DuckDuckGo (ghcr.io/mudler/mcps/duckduckgo)

Methods:
- `search(query)`

Rules:
- Use for external info gathering.
- Summarize findings in `planning.md`.

---

## Memory (ghcr.io/mudler/mcps/memory)

Methods:
- `add(key, value)`
- `get(key)`
- `delete(key)`
- `list()`

Rules:
- Store reusable patterns and decisions.
- Retrieve memory before reinventing solutions.

---

## Todo (ghcr.io/mudler/mcps/todo)

Methods:
- `add(text)`
- `update(id, text)`
- `complete(id)`
- `delete(id)`
- `list()`
- `group(name)`
- `setDependency(id, dependsOn)`

Rules:
- Maintain TODOs for all tasks.
- Keep TODOs synced with filesystem changes.

---

## Codemogger (ghcr.io/mudler/mcps/codemogger)

Methods:
- `generate(spec)`
- `refactor(path)`
- `analyze(path)`
- `fix(path)`
- `explain(path)`
- `createProjectStructure(spec)`

Rules:
- Use `generate` only after planning.
- Use `refactor` only on verified code files.
- Use `analyze` before modifying existing code.
- Ensure `.py` files contain valid code only.

---

## LocalRecall (ghcr.io/mudler/mcps/localrecall)

Methods:
- `addDocument(content, tags)`
- `search(query)`
- `removeDocument(id)`
- `embed(content)`

Rules:
- Store reusable knowledge.
- Search before creating new patterns.

---

## PDF (ghcr.io/mudler/mcps/pdf)

Methods:
- `extractText(path)`
- `extractImages(path)`
- `metadata(path)`

Rules:
- Extract requirements or specs.
- Summarize into `planning.md`.

---

## Image (ghcr.io/mudler/mcps/image)

Methods:
- `metadata(path)`
- `resize(path, params)`
- `convert(path, format)`
- `extractText(path)` (OCR)

Rules:
- Keep assets organized.
- Use OCR for embedded text.

---

## Audio (ghcr.io/mudler/mcps/audio)

Methods:
- `transcribe(path)`
- `metadata(path)`
- `convert(path, format)`

Rules:
- Transcribe spoken notes.
- Store transcripts in planning or docs.

---

## Browser (ghcr.io/mudler/mcps/browser)

Methods:
- `navigate(url)`
- `extract(selector)`
- `screenshot(url)`
- `evaluate(script)`

Rules:
- Use for documentation and data gathering.
- Validate scraped content.

---

## Git (ghcr.io/mudler/mcps/git)

Methods:
- `init(path)`
- `status(path)`
- `add(path)`
- `commit(message)`
- `diff(path)`
- `log(path)`
- `branch(name)`
- `merge(branch)`

Rules:
- Commit only verified changes.
- Use branches for major work.

---

## SQLite (ghcr.io/mudler/mcps/sqlite)

Methods:
- `query(sql)`
- `createTable(sql)`
- `insert(sql)`
- `update(sql)`
- `delete(sql)`

Rules:
- Keep schema in `.sql` or `.md`.
- Document important queries.

---

## Cron (ghcr.io/mudler/mcps/cron)

Methods:
- `schedule(task, cronExpression)`
- `list()`
- `remove(id)`

Rules:
- Document scheduled jobs.
- Use for maintenance tasks.

---

## SystemInfo (ghcr.io/mudler/mcps/systeminfo)

Methods:
- `cpu()`
- `ram()`
- `gpu()`
- `disk()`
- `environment()`

Rules:
- Check resources before heavy tasks.
- Record constraints in planning.

---

## Final Expectations

The Super Agent MUST:
- Use **all tool methods** correctly.
- Keep planning in `planning.md`.
- Keep TODOs synced with reality.
- Enforce preconditions before acting.
- Maintain a clean filesystem.
- Produce valid code only.
- Document decisions and changes.

This SKILL.md defines a disciplined, production-grade agent for Mudler’s MCP ecosystem.
