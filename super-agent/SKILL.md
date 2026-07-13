---
name: super-agent
description: Master orchestration skill that teaches the LLM how to use all MCP tools.
allowed-tools: filesystem, bash, think, duckduckgo, memory, todo, codemogger, localrecall, pdf, image, audio, browser, git, sqlite, cron, systeminfo
---

# 🧠 Super-Agent Skill
### Master Orchestration Skill for LocalAI MCP Tools

The **Super-Agent** skill provides a unified orchestration layer for all available MCP tools in LocalAI. It teaches the model how to intelligently select, combine, and execute tools to solve complex tasks, automate workflows, manage memory, perform reasoning, and interact with the system. This skill acts as a meta-controller, enabling high-level planning and multi-step execution.

---

## 🚀 Features

### Full MCP Tool Integration
Super-Agent supports all major MCP tools:

- filesystem — read/write files, inspect directories  
- bash — execute shell commands, run scripts  
- think — deep reasoning and chain-of-thought  
- duckduckgo — web search  
- memory — persistent long-term memory  
- todo — task management  
- codemogger — code generation, refactoring, analysis  
- localrecall — embeddings + semantic search  
- pdf — PDF extraction and parsing  
- image — image processing and metadata  
- audio — transcription and audio conversion  
- browser — headless web browsing and scraping  
- git — version control operations  
- sqlite — local database queries  
- cron — scheduled tasks  
- systeminfo — system resource inspection  

---

## 🎯 Purpose

Super-Agent is designed to:

- Automate complex workflows  
- Break down tasks into actionable steps  
- Use the correct tool for each job  
- Maintain memory and context  
- Perform deep reasoning  
- Search and analyze documents  
- Execute code and scripts  
- Manage projects and repositories  
- Interact with the local system safely  
- Provide structured responses and plans  

---

## 🧩 Tool Usage Guidelines

### filesystem
Use for reading, writing, editing, or organizing files.

### bash
Use for executing commands, running scripts, or interacting with the OS.

### think
Use for planning, reasoning, or multi-step problem solving.

### duckduckgo
Use for searching the web or retrieving external information.

### memory
Use for storing important facts or retrieving long-term knowledge.

### todo
Use for managing tasks, subtasks, and workflows.

### codemogger
Use for generating, refactoring, or analyzing code.

### localrecall
Use for embedding documents and performing semantic search.

### pdf / image / audio
Use for processing media files.

### browser
Use for dynamic web interactions or scraping.

### git
Use for version control, commits, diffs, branches, and repo management.

### sqlite
Use for structured data storage and queries.

### cron
Use for scheduling recurring tasks.

### systeminfo
Use for inspecting CPU, RAM, GPU, disk, and environment details.

---

## 📘 Examples

### Read a file
Use filesystem.readFile to inspect `/main/project/notes.txt`.

### Run a shell command
Use bash.execute to run `ls -la /main`.

### Search the web
Use duckduckgo.search for “best linux laptops 2026”.

### Store memory
Use memory.store to save: “User prefers Intel Arc GPU for LocalAI”.

### Generate code
Use codemogger.generate to create a Python script that parses JSON.

### Semantic search
Use localrecall.search to find references to “audio routing” in documents.

### Process a PDF
Use pdf.extractText on `/main/docs/manual.pdf`.

### Schedule a task
Use cron.schedule to run `backup.sh` every day at 3 AM.

---

## 🔒 Safety & Constraints

- Avoid destructive bash commands unless explicitly requested  
- Use filesystem responsibly (no deleting system files)  
- Use browser only for safe, non-authenticated pages  
- Use git operations carefully to avoid overwriting user work  
- Use cron only for tasks the user approves  
- Use memory only for relevant, non-sensitive information  

---

## 📦 Version

Super-Agent v1.0.0  
Compatible with LocalAI v4.6+

---

## 👤 Author

falsejaguar  
GitHub: https://github.com/falsejaguar/super-skill

---

# 💻 Developer Stack
### Tools for coding, debugging, building, testing, and automation

The Developer Stack provides a focused set of tools for software development workflows.

## Included Tools

- filesystem — project file management  
- bash — build scripts, test runners, automation  
- git — version control  
- codemogger — code generation and refactoring  
- sqlite — local database queries  
- pdf — documentation extraction  
- image — asset processing  
- think — reasoning for debugging  

## Usage Patterns

- Inspect project structure before making changes  
- Use git for safe commits and diffs  
- Use codemogger for code generation and refactoring  
- Use bash for builds, tests, and automation  
- Use filesystem for edits and organization  

---

# 🤖 AI Agent Stack
### Tools for autonomous workflows, planning, memory, and reasoning

The AI Agent Stack enables long-running, self-directed tasks and agentic behavior.

## Included Tools

- think — chain-of-thought reasoning  
- memory — persistent knowledge  
- todo — task lists and workflows  
- cron — scheduled jobs  
- localrecall — semantic search over documents  
- browser — dynamic web automation  
- duckduckgo — web search  
- systeminfo — environment awareness  

## Usage Patterns

- Break tasks into subtasks using think and todo  
- Store important facts in memory for future use  
- Use cron for recurring or delayed tasks  
- Use localrecall to search across stored documents  
- Use browser for dynamic pages and automation  
- Use duckduckgo for external information gathering  

---

# 🎨 Creative Stack
### Tools for media, assets, and creative workflows

The Creative Stack focuses on handling media and creative assets.

## Included Tools

- image — editing, metadata, resizing  
- audio — transcription, conversion, analysis  
- pdf — extracting text from creative docs  
- filesystem — organizing assets and projects  
- think — creative reasoning and planning  

## Usage Patterns

- Process images for thumbnails, concept art, or assets  
- Transcribe and convert audio for notes or editing  
- Extract text from PDFs for scripts, outlines, or references  
- Organize creative projects with filesystem  

---

# 🌍 Worldbuilding Stack
### Tools for lore creation, universe design, and narrative structure

The Worldbuilding Stack supports complex fictional universes and long-form narrative design.

## Included Tools

- memory — persistent lore and canon  
- think — deep narrative reasoning and planning  
- filesystem — storing world files, notes, and maps  
- localrecall — semantic search across lore documents  
- todo — tracking story arcs, character threads, and plotlines  

## Usage Patterns

- Store character bios, locations, and timelines in memory  
- Use localrecall to find references to characters, events, or places  
- Use todo to track unresolved plot threads and future arcs  
- Use filesystem to organize world files, maps, and documents  
- Use think to plan multi-arc stories and complex relationships  

---

# 🏁 End of Document
This is the complete unified Markdown for the Super-Agent skill and all associated stacks. Paste this entire block into the Skill Content window in LocalAI.