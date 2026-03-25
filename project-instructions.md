This file is a merged representation of a subset of the codebase, containing files not matching ignore patterns, combined into a single document by Repomix.

# File Summary

## Purpose
This file contains a packed representation of a subset of the repository's contents that is considered the most important context.
It is designed to be easily consumable by AI systems for analysis, code review,
or other automated processes.

## File Format
The content is organized as follows:
1. This summary section
2. Repository information
3. Directory structure
4. Repository files (if enabled)
5. Multiple file entries, each consisting of:
  a. A header with the file path (## File: path/to/file)
  b. The full contents of the file in a code block

## Usage Guidelines
- This file should be treated as read-only. Any changes should be made to the
  original repository files, not this packed version.
- When processing this file, use the file path to distinguish
  between different files in the repository.
- Be aware that this file may contain sensitive information. Handle it with
  the same level of security as you would the original repository.
- Pay special attention to the Repository Description. These contain important context and guidelines specific to this project.

## Notes
- Some files may have been excluded based on .gitignore rules and Repomix's configuration
- Binary files are not included in this packed representation. Please refer to the Repository Structure section for a complete list of file paths, including binary files
- Files matching these patterns are excluded: .gitignore, import-gemini.mjs, project-instructions.md, repomix-agentwiki.md, repomix.config.json, repomix.seed.config.json, package*.json, node_modules/**, docs/**, Agents.todo.md
- Files matching patterns in .gitignore are excluded
- Files matching default ignore patterns are excluded
- Files are sorted by Git change count (files with more changes are at the bottom)

# User Provided Header
## 🚀 AI AGENT DOC-AS-CODE: SEED INSTRUCTIONS
This is the base workflow and example structure for a NEW project. Follow these rules to set up your own Doc-as-Code architecture.

# Directory Structure
```
AGENT-RULES.md
example/Agents.todo.md
example/docs/domains/auth/01-login.md
example/docs/tech/database/01-postgres-schema.md
example/docs/tech/security/01-rate-limiting.md
README.md
```

# Files

## File: AGENT-RULES.md
```markdown
# 🛑 AI AGENT MASTER RULES & POLICY

> **CRITICAL:** You are interacting with an automated Doc-as-Code workflow. Read these rules carefully to understand your current role.

## 1. Core Directives
- **Language:** The working language for all documentation, commit messages, and code comments is **English**.
- **Context is King:** Always read the linked Markdown documents to understand business and technical constraints.

## 2. Agent Roles (Planner / Maker / Checker)
We enforce a strict separation of concerns. Identify which role you are currently executing based on the user's prompt.

### Role 1: Planner Agent ("Architect / Update Target State")
- **Goal:** Collaborate with the human to define the target state ("SOLL-Zustand").
- **Action:** Update or create Markdown documentation in the `docs/` folder with functional and technical requirements.
- **Task Derivation:** After updating the documentation, derive clear, actionable implementation steps and append them to the top of `Agents.todo.md`.
  - *Format:* `- [ ] TODO: [Actionable Description] -> [Link to specific doc]`

### Role 2: Implementation Agent ("Maker")
- **Goal:** Execute tasks and write code.
- **Action:** Pick the top-most unassigned `[ ] TODO` task from `Agents.todo.md`. Implement the feature.
- **Documentation:** Document your technical decisions (e.g., libraries used, architecture choices) in the corresponding feature markdown file.
- **Task Update:** Change the task text in `Agents.todo.md`. Do **NOT** check the box.
  - *Example:* `- [ ] (Ready for Review) TODO: Implement Login -> [Link](...)`

### Role 3: Review Agent ("Checker")
- **Goal:** Quality assurance and validation.
- **Action:** Pick the top-most task marked as `(Ready for Review)` in `Agents.todo.md`. Validate the code strictly against the requirements in the linked markdown document.
- **Task Update (Pass):** If code is flawless:
  - *Example:* `- [x] TODO: Implement Login -> [Link](...)`
- **Task Update (Fail):** If code fails, change status back and write required fixes into the linked markdown document under "Review Notes".
  - *Example:* `- [ ] (Needs Fix) TODO: Implement Login -> [Link](...)`
```

## File: example/Agents.todo.md
```markdown
# 📋 Example Task Queue
- [ ] **TODO:** Implement User Login -> [Link](docs/domains/auth/01-login.md)
```

## File: example/docs/domains/auth/01-login.md
```markdown
# Example Document
This is just a placeholder to show how domains work.
```

## File: example/docs/tech/database/01-postgres-schema.md
```markdown
---
domain: technical
topic: database
status: open
---

# Technical Concept: PostgreSQL User Schema

## 🛠 Technical Details & Architecture
- **Table:** `users`
- **Encryption:** `bcrypt` for passwords (Salting Rounds: 10).
- **Schema:**
  - `id` (UUID, Primary Key, Auto-Generate)
  - `email` (Varchar, Unique, Not Null)
  - `password_hash` (Varchar, Not Null)
  - `email_verified` (Boolean, Default: false)
  - `created_at` (Timestamp with Timezone)
```

## File: example/docs/tech/security/01-rate-limiting.md
```markdown
---
domain: technical
topic: security
status: draft
---

# Technical Concept: API Rate Limiting

## 🛠 Target State Specifications
To prevent brute-force attacks on the login route, we must implement rate limiting.
- **Limit:** Max 5 failed login attempts per IP within 15 minutes.
- **Storage:** Use Redis as an in-memory store for counters.
```

## File: README.md
```markdown
# 🧠 AI Agent "Doc-as-Code" Architecture

Welcome to the AI Agent integration repository. This project uses a Markdown-based workflow to manage requirements, architecture, and task execution for Autonomous AI Agents.

👉 **[View the compiled Master Instructions for AI Agents here](project-instructions.md)**

## 🎯 The Concept
Instead of using external ticket systems, we use a **Wiki-based Doc-as-Code approach**. 
AI models understand the *entire* system architecture by reading the bundled Markdown context before writing a single line of code. 

*Note: The maintainer compiles the context into `project-instructions.md` before committing. This file acts as the single entry point for any AI Agent.*

## 🤖 The 3 AI Agent Roles
The detailed rules for the AI are located in `AGENT-RULES.md`.
1. **Planner Agent ("Target State / Architect"):** Collaborates with humans to update the documentation and derives actionable TODOs.
2. **Maker Agent ("Implementation"):** Writes the code, updates the docs with technical decisions, and marks tasks as `(Ready for Review)`.
3. **Checker Agent ("Reviewer"):** Reviews the code against the Markdown requirements and checks off the task `[x]`.
```
