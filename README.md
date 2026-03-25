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
