# Phase 2 — Git and Project Structure
## AI-Powered Expense Tracker: Learning Checklist

**Project:** AI-Powered Expense Tracker  
**Phase:** 2 of the learning roadmap  
**Tasks:** 15–17  
**Prerequisites:** Phase 1 — Python Fundamentals  
**Learning approach:** Learn → Practise → Implement → Review

---

# Phase 2 Objective

Transform the command-line expense tracker into a properly organised, version-controlled Python project that is safe to share publicly.

By the end of this phase, you should understand how developers track changes, organise application code, document projects, and manage configuration without exposing secrets.

## Ground Rules

- Complete one task at a time.
- Use the existing expense tracker; don't create a separate project unnecessarily.
- Understand every Git command before running it.
- Make small, meaningful commits instead of committing everything at once.
- Never commit passwords, API keys, tokens, or other secrets.
- Review your work before moving to the next task.

---

# Task 15 — Initialise Git and Make Clear, Small Commits

## Learning objectives

Understand version control and learn how to maintain a useful history of changes to your project.

### Topics to learn

**1. Git fundamentals**
- What version control is and why developers use it.
- Difference between Git and GitHub.
- Local repositories versus remote repositories.
- Working directory, staging area, and repository history.
- What a commit represents.

**2. Basic Git commands**
- `git init` — initialise a repository.
- `git status` — inspect the current working tree.
- `git add` — stage changes.
- `git commit` — save a snapshot.
- `git log` — inspect commit history.
- `git diff` — inspect changes.
- `git restore` — discard selected unstaged changes.
- `git branch` — inspect and manage branches.
- `git remote -v` — inspect remote repositories.
- `git push` and `git pull` — synchronise with a remote repository.

**3. Commit practices**
- Write meaningful commit messages.
- Make small commits that represent logical changes.
- Understand staged versus unstaged changes.
- Review changes before committing.
- Understand what a commit does and does not save.

### Practical exercises

- [ ] Navigate to the root of the expense tracker project.
- [ ] Inspect the current repository using `git status`.
- [ ] Determine whether Git is already initialised.
- [ ] If needed, initialise Git with `git init`.
- [ ] Inspect the current branch.
- [ ] Review changes using `git diff`.
- [ ] Stage a specific file with `git add`.
- [ ] Create a commit with a meaningful message.
- [ ] Inspect the commit using `git log --oneline`.
- [ ] Make a small change and create another commit.
- [ ] Practise checking the working tree before committing.
- [ ] Inspect configured remote repositories, if any.

### Example workflow

```bash
git status
git diff
git add main.py
git status
git commit -m "Add expense tracker entry point"
git log --oneline
```

Run these commands from your project directory. Only use the example commit if the change actually matches the message.

### Mini-project exercise

Create a short sequence of meaningful commits representing actual improvements to your expense tracker, such as:
- Adding the application entry point.
- Adding expense-related functionality.
- Improving input validation.

If your project already has a Git history, continue using it instead of reinitialising the repository.

### Completion criteria

- [ ] Can explain the purpose of Git and GitHub.
- [ ] Understands the working directory, staging area, and commit history.
- [ ] Can stage selected changes and commit them.
- [ ] Can inspect differences before committing.
- [ ] Can read the recent commit history.
- [ ] Can explain the difference between local commits and pushing to GitHub.

**Deliverable:** A project with a clear, meaningful Git history.

---

# Task 16 — Clean Application Structure, README and `.gitignore`

## Learning objectives

Organise the application so that its code, documentation, configuration, and supporting files have clear responsibilities.

### Topics to learn

**1. Project structure**
- What the project root directory is.
- Separating application code from documentation and configuration.
- Why files should have clear names and responsibilities.
- Why unnecessary nesting and oversized files make projects harder to maintain.
- How to navigate a project using the terminal.

**2. README documentation**
- What a `README.md` file is for.
- Markdown headings, lists, links, code blocks, and tables.
- Writing project descriptions and setup instructions.
- Documenting prerequisites and commands.
- Keeping documentation consistent with the actual application.

**3. `.gitignore`**
- What Git tracks and what it ignores.
- Why virtual environments should generally not be committed.
- Ignoring Python cache files.
- Ignoring local environment-variable files.
- Understanding that `.gitignore` does not untrack files already committed.

### Practical exercises

- [ ] Inspect the current project structure.
- [ ] Identify the application's entry point.
- [ ] Separate application code from unrelated temporary files.
- [ ] Create or update `README.md`.
- [ ] Add a project title and description.
- [ ] Document the purpose and current features.
- [ ] Document Python prerequisites.
- [ ] Write instructions for running the application.
- [ ] Create a `.gitignore` file.
- [ ] Ignore Python cache files and virtual environments.
- [ ] Ignore local `.env` files.
- [ ] Check whether generated files are being tracked.
- [ ] Run `git status` and review the result.
- [ ] Commit the structural and documentation changes.

### Suggested initial project structure

```text
ai-expense-tracker/
├── main.py
├── README.md
├── .gitignore
├── requirements.txt
└── .venv/
```

This is an illustrative starting structure, not a requirement to create every file immediately. The virtual environment should exist locally but should not be committed to Git.

As the application grows, we can introduce separate modules and tests when they are useful.

### Suggested `.gitignore`

```gitignore
# Python cache files
__pycache__/
*.py[cod]

# Virtual environments
.venv/
venv/
env/

# Local environment variables and secrets
.env
.env.*

# Allow an example configuration template
!.env.example

# Test and tooling caches
.pytest_cache/
.mypy_cache/
.ruff_cache/

# Editor and operating-system files
.vscode/
.DS_Store
Thumbs.db
```

Adjust this file to match the project's needs. If a real secret has already been committed, adding it to `.gitignore` alone does not remove it from Git history.

### README requirements

Your `README.md` should eventually explain:

- What the AI Expense Tracker does.
- Current features.
- Prerequisites.
- How to set up the project.
- How to run the application.
- How to run tests once tests exist.
- How configuration is handled.
- Planned features, if useful.

Do not document features that have not been implemented as though they already work.

### Completion criteria

- [ ] The project has a clear root directory.
- [ ] The application entry point is easy to identify.
- [ ] `README.md` explains the project and how to run it.
- [ ] `.gitignore` excludes the virtual environment and common generated files.
- [ ] Local configuration files are excluded from Git.
- [ ] The project status contains no unintended generated files.
- [ ] The changes are committed.

**Deliverable:** An organised, documented project with a suitable `.gitignore`.

---

# Task 17 — Environment Variables and Secret Management

## Learning objectives

Separate application configuration from source code and learn how to protect sensitive values when working with Git and external services.

### Topics to learn

**1. Configuration fundamentals**
- What application configuration is.
- Why configuration should not be hard-coded.
- Difference between source code and runtime configuration.
- Development versus production configuration.
- What environment variables are.

**2. Working with environment variables**
- Reading environment variables using `os.environ` and `os.getenv()`.
- Providing default values where appropriate.
- Handling missing configuration.
- Understanding how environment variables are inherited by processes.
- Setting a variable in a Linux shell.
- Understanding the difference between a shell variable and an exported environment variable.

**3. Secret management**
- What counts as a secret: passwords, tokens, private credentials, and API keys.
- Why secrets must not be committed to Git.
- Why public repositories require particular care.
- Why `.gitignore` helps but is not a complete security solution.
- Why real secrets must be revoked or rotated if exposed.
- Why example configuration files must contain placeholders rather than real credentials.

**4. `.env` files**
- What a `.env` file is.
- How applications can load values from a `.env` file using a suitable library.
- Why `.env` files should remain local.
- The purpose of `.env.example`.
- The difference between loading configuration and securing secrets.

### Practical exercises

- [ ] Create a simple configuration value in your terminal.
- [ ] Export an environment variable.
- [ ] Read it in Python using `os.getenv()`.
- [ ] Print a harmless configuration value.
- [ ] Test what happens when an environment variable is missing.
- [ ] Add a sensible default where appropriate.
- [ ] Create a local `.env` file for a harmless development setting.
- [ ] Create a `.env.example` containing placeholder values.
- [ ] Verify that `.env` is ignored by Git.
- [ ] Verify that `.env.example` can be tracked.
- [ ] Inspect `git status` before committing.
- [ ] Explain why real credentials should never appear in source code.

### Exercise 1 — Read an environment variable

In your terminal:

```bash
export APP_ENV=development
python3 main.py
```

Inside a temporary test script, try:

```python
import os

environment = os.getenv("APP_ENV")
print(environment)
```

Expected output when the variable is exported in the same shell:

```text
development
```

The variable is available to child processes launched from that shell. It will not automatically persist across every new terminal session.

### Exercise 2 — Handle missing configuration

Try reading a variable that hasn't been set:

```python
import os

currency = os.getenv("APP_CURRENCY", "INR")
print(currency)
```

Expected output if `APP_CURRENCY` is not set:

```text
INR
```

This demonstrates a default configuration value.

### Exercise 3 — Separate local configuration from the example

Create a local `.env` file:

```dotenv
APP_ENV=development
APP_CURRENCY=INR
```

Create a tracked `.env.example` file:

```dotenv
APP_ENV=development
APP_CURRENCY=INR
```

These examples contain no secrets. Later, when the application needs an API key, use a placeholder in the example file rather than an actual key.

A `.env` file is not loaded automatically by Python. A later task can introduce a library such as `python-dotenv` if the project needs it.

### Completion criteria

- [ ] Can explain what an environment variable is.
- [ ] Can read configuration using `os.getenv()`.
- [ ] Understands default values and missing configuration.
- [ ] Can distinguish source code from runtime configuration.
- [ ] Knows why `.env` should be ignored by Git.
- [ ] Can create a safe `.env.example`.
- [ ] Can verify that local configuration is not staged or committed.
- [ ] Understands that `.gitignore` cannot erase secrets already committed.

**Deliverable:** An application that reads configuration from environment variables and keeps local configuration out of version control.

---

# Phase 2 Final Checkpoint

Before moving to Phase 3, verify the following.

## Git
- [ ] Git is configured and working.
- [ ] You can inspect changes and create small commits.
- [ ] You understand local commits versus remote pushes.
- [ ] Your project history is understandable.

## Project organisation
- [ ] Your project has a clear structure.
- [ ] `README.md` explains what the application does and how to run it.
- [ ] `.gitignore` excludes generated files and local configuration.
- [ ] The virtual environment is not tracked by Git.

## Configuration and security
- [ ] The application can read environment variables.
- [ ] Missing configuration is handled appropriately.
- [ ] `.env.example` contains only safe example values.
- [ ] Real credentials are not committed.
- [ ] You know what to do if a secret is accidentally exposed.

## Final deliverable

A clean, documented, version-controlled expense tracker that can be shared publicly without accidentally publishing local environment files or credentials.

---

# Progress Tracker

| Task | Topic | Status |
|---|---|---|
| 15 | Git and meaningful commits | Not started |
| 16 | Project structure, README and `.gitignore` | Not started |
| 17 | Environment variables and secret management | Not started |

**Phase checkpoint:** The project is organised, version-controlled, and safe to share publicly.

## What comes next?

**Phase 3 — HTTP and APIs with FastAPI.**

We'll learn client-server communication, HTTP requests and responses, JSON, status codes, Pydantic models, and CRUD endpoints. We'll build on the project we've already organised rather than starting over.
