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
