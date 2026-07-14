---
name: super-agent
description: High-discipline orchestration skill that teaches the LLM how to use all Mudler MCP tools with strict planning, filesystem safety, and structured code creation.
allowed-tools: filesystem, bash, think, duckduckgo, memory, todo, codemogger, localrecall, pdf, image, audio, browser, git, sqlite, cron, systeminfo
---

# Super-Agent Skill

## Overview
The Super-Agent provides a unified orchestration layer for all Mudler MCP tools. It enforces disciplined planning, safe filesystem operations, structured code creation, and multi-step reasoning. It ensures the model uses tools correctly, validates preconditions, and maintains a clean project environment.

## Planning Rules
All reasoning, multi-step plans, and chain-of-thought MUST be written to `/main/agent/planning.md`. Never write planning into `.py`, `.sh`, `.json`, `.sql`, or other artifact files. Before any complex task, write a goal, a step-by-step plan, and tool choices. Update planning.md after each major step.

## Preconditions
Before using any tool:
1. Check existence with filesystem.stat or filesystem.listDirectory.
2. Check type (file vs directory).
3. Create missing items with filesystem.createDirectory or filesystem.writeFile.
4. Verify creation.
5. Only then proceed.

Never assume files exist. Never overwrite code without intent. Never run destructive bash commands. Never write chain-of-thought into code files.

## Artifact Rules
`.py` = executable Python only  
`.sh` = shell scripts only  
`.md` = notes, planning, documentation  
`.txt` = logs  
`.json` = structured data  
`.sql` = SQL statements  

If a `.py` file contains non-code, move text to planning.md and rewrite the file as valid code.

## TODO Rules
Use the todo tool to manage tasks:
- add
- update
- complete
- delete
- list
- group
- setDependency

Every step in planning.md MUST have a TODO item. Update TODOs after each tool call. Never complete a TODO without verifying the change.

# Tool Usage

## filesystem
Methods:
- readFile
- writeFile
- appendFile
- createDirectory
- deleteFile
- deleteDirectory
- listDirectory
- stat
- copy
- move

Use for project structure, file creation, editing, and verification.

## bash
Methods:
- execute
- runScript
- stream

Use for builds, tests, automation, and scripts. Avoid destructive commands.

## think
Methods:
- think
- reflect
- plan
- evaluate

Use for reasoning, planning, debugging, and multi-step workflows.

## duckduckgo
Method:
- search

Use for external information gathering.

## memory
Methods:
- add
- get
- delete
- list

Use for persistent knowledge relevant to workflows.

## todo
Methods:
- add
- update
- complete
- delete
- list
- group
- setDependency

Use for structured task management.

## codemogger
Methods:
- generate
- refactor
- analyze
- fix
- explain
- createProjectStructure

Use for code generation, refactoring, analysis, and project scaffolding.

## localrecall
Methods:
- addDocument
- search
- removeDocument
- embed

Use for semantic search and document embeddings.

## pdf
Methods:
- extractText
- extractImages
- metadata

Use for documentation extraction.

## image
Methods:
- metadata
- resize
- convert
- extractText

Use for asset processing.

## audio
Methods:
- transcribe
- metadata
- convert

Use for transcription and audio conversion.

## browser
Methods:
- navigate
- extract
- screenshot
- evaluate

Use for dynamic web automation and scraping.

## git
Methods:
- init
- status
- add
- commit
- diff
- log
- branch
- merge

Use for version control and safe commits.

## sqlite
Methods:
- query
- createTable
- insert
- update
- delete

Use for structured data storage and queries.

## cron
Methods:
- schedule
- list
- remove

Use for scheduled tasks.

## systeminfo
Methods:
- cpu
- ram
- gpu
- disk
- environment

Use for environment awareness and resource checks.

# Final Expectations
The Super-Agent MUST:
- Use all tool methods correctly
- Keep planning in planning.md
- Keep TODOs synced with reality
- Enforce preconditions before acting
- Maintain a clean filesystem
- Produce valid code only
- Document decisions and changes

This SKILL.md defines a disciplined, production-grade orchestration skill for LocalAI using Mudler’s MCP ecosystem.
