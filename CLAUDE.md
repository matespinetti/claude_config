## 🔄 Project Awareness & Context
- **Always read `PLANNING.md`** at the start of a new conversation to understand the project's architecture, goals, style, and constraints.
- **Check `TASK.md`** before starting a new task. If the task isn't listed, add it with a brief description and today's date.
- **Use consistent naming conventions, file structure, and architecture patterns** as described in `PLANNING.md`.
- **Follow the project's established development environment setup** (virtual environments, containers, package managers, etc.) as documented.

## 🧱 Code Structure & Modularity
- **Never create a file longer than 500 lines of code.** If a file approaches this limit, refactor by splitting it into modules or helper files.
- **Organize code into clearly separated modules**, grouped by feature or responsibility following the project's established patterns.
- **Use clear, consistent imports/includes** following the language's best practices and project conventions.
- **Follow the project's dependency management approach** (package.json, requirements.txt, Cargo.toml, etc.).

## 🧪 Testing & Reliability
- **Always create unit tests for new features** using the project's established testing framework.
- **After updating any logic**, check whether existing tests need to be updated. If so, do it.
- **Tests should live in the designated test directory** following the project's structure conventions.
  - Include at least:
    - 1 test for expected use
    - 1 edge case
    - 1 failure case

## ✅ Task Completion
- **Mark completed tasks in `TASK.md`** immediately after finishing them.
- Add new sub-tasks or TODOs discovered during development to `TASK.md` under a "Discovered During Work" section.

## 📎 Style & Conventions
- **Follow the language's standard style guide** (PEP8 for Python, PSR for PHP, Standard for JavaScript, etc.).
- **Use the project's established formatter and linter** configuration.
- **Include type annotations/hints** where the language supports them and the project uses them.
- **Write documentation comments for every function** using the language's standard format:
  - Python: Google/Sphinx docstrings
  - JavaScript: JSDoc
  - Java: Javadoc
  - C#: XML documentation
  - Rust: /// comments
  - Go: Standard Go comments

## 📚 Documentation & Explainability
- **Update `README.md`** when new features are added, dependencies change, or setup steps are modified.
- **Comment non-obvious code** and ensure everything is understandable to a mid-level developer.
- When writing complex logic, **add inline comments** explaining the reasoning, not just the implementation.

## 🧠 AI Behavior Rules
- **Never assume missing context. Ask questions if uncertain.**
- **Never hallucinate libraries, frameworks, or APIs** – only use known, verified packages for the target language.
- **Always confirm file paths, module names, and dependencies** exist before referencing them in code or tests.
- **Never delete or overwrite existing code** unless explicitly instructed to or if part of a task from `TASK.md`.
- **Respect the project's architecture decisions** and ask before introducing new patterns or significant structural changes.