# AI-Powered Expense Tracker — Step-by-Step Roadmap

A brick-by-brick project to refresh Python, learn APIs and backend development, work with a database, integrate an AI feature, test the application, and deploy it.

**How we'll work:** Complete one task at a time. Start with Task 1 only; don't skip ahead. We'll review your solution together before moving on.

## Project goal

Build an expense tracker that lets a user record and review expenses, categorise spending, view summaries, and optionally ask an AI assistant questions about their spending.

## Planned technology

- **Language:** Python
- **API framework:** FastAPI
- **Data validation:** Pydantic
- **Database:** SQLite first, then PostgreSQL
- **Database access:** SQLAlchemy
- **Testing:** pytest and FastAPI's test client
- **AI integration:** An LLM API, added only after the core application works
- **Packaging and deployment:** Git, environment variables, Docker, and a suitable hosting platform

We'll choose exact library versions and a hosting provider when we reach those tasks. You don't need to install everything at the start.

---

## Phase 1 — Refresh Python fundamentals

- [ ] **Task 1:** Set up the project folder and Python environment; run a simple Python script.
- [ ] **Task 2:** Review variables, basic data types, input, output, and type conversion.
- [ ] **Task 3:** Practise strings, formatting, and common string methods.
- [ ] **Task 4:** Review conditions (`if`, `elif`, `else`) and Boolean logic.
- [ ] **Task 5:** Review loops (`for`, `while`) and iteration.
- [ ] **Task 6:** Practise lists, tuples, sets, and dictionaries.
- [ ] **Task 7:** Write functions; understand parameters, return values, scope, and defaults.
- [ ] **Task 8:** Handle errors with `try`, `except`, and `finally`; learn to read tracebacks.
- [ ] **Task 9:** Read and write files; work with JSON data.
- [ ] **Task 10:** Review modules, imports, virtual environments, and installing packages with `pip`.
- [ ] **Task 11:** Practise comprehensions, sorting, filtering, and useful built-in functions.
- [ ] **Task 12:** Learn classes and objects at a practical level; use dataclasses where helpful.
- [ ] **Task 13:** Build a command-line expense tracker that adds expenses, lists them, and calculates totals.
- [ ] **Task 14:** Refactor the command-line tracker into small functions and add input validation.

**Phase checkpoint:** You can write and debug a small Python program without copying every line from a tutorial.

## Phase 2 — Git and project structure

- [ ] **Task 15:** Initialise a Git repository and make clear, small commits.
- [ ] **Task 16:** Create a clean application structure and a `README.md`; add a `.gitignore`.
- [ ] **Task 17:** Learn configuration through environment variables and keep secrets out of Git.

**Phase checkpoint:** Your project is organised, version-controlled, and safe to share publicly.

## Phase 3 — HTTP and APIs with FastAPI

- [ ] **Task 18:** Understand client/server basics, HTTP requests and responses, JSON, and common status codes.
- [ ] **Task 19:** Create a FastAPI application and run it locally.
- [ ] **Task 20:** Explore automatic API documentation and make a request to a test endpoint.
- [ ] **Task 21:** Define Pydantic request and response models; validate incoming data.
- [ ] **Task 22:** Add an endpoint to create an expense.
- [ ] **Task 23:** Add endpoints to list, retrieve, update, and delete expenses.
- [ ] **Task 24:** Add query parameters for filtering by category, date, and amount; implement pagination.
- [ ] **Task 25:** Return appropriate status codes and handle invalid input and missing records consistently.

**Phase checkpoint:** You have a working REST API, initially using temporary in-memory data.

## Phase 4 — Database persistence

- [ ] **Task 26:** Learn basic SQL: tables, rows, primary keys, queries, inserts, updates, and deletes.
- [ ] **Task 27:** Connect the application to SQLite and define the expense data model with SQLAlchemy.
- [ ] **Task 28:** Replace in-memory storage with database operations.
- [ ] **Task 29:** Add database migrations and understand how to change the schema safely.
- [ ] **Task 30:** Add PostgreSQL configuration and verify the app works with a PostgreSQL database.

**Phase checkpoint:** Expenses persist after restarting the application.

## Phase 5 — Useful features and reliability

- [ ] **Task 31:** Add expense categories, dates, descriptions, and sensible validation rules.
- [ ] **Task 32:** Build summary endpoints for total spending, category breakdowns, and monthly trends.
- [ ] **Task 33:** Add automated tests for core functions, API endpoints, validation, and database behaviour.
- [ ] **Task 34:** Improve error handling, logging, and input validation; review common security risks.
- [ ] **Task 35:** Add basic authentication and ensure users can access only their own expenses.

**Phase checkpoint:** The main features are tested, and one user's data is separated from another's.

## Phase 6 — AI feature

- [ ] **Task 36:** Learn the basics of calling an external API, handling timeouts, errors, and rate limits.
- [ ] **Task 37:** Add an AI spending-insights endpoint that uses the user's expense summaries to answer questions or produce a short review.
- [ ] **Task 38:** Protect API keys with environment variables, limit the data sent to the model, and test failure cases.

**Phase checkpoint:** The AI feature works without exposing secrets or sending unnecessary personal data.

## Phase 7 — Ship the project

- [ ] **Task 39:** Create a Dockerfile, run the application in a container, and document local setup.
- [ ] **Task 40:** Deploy the application and database to a suitable host; verify the live API, add final documentation, and record a short demo.

**Final checkpoint:** You have a deployed, documented project that you can explain in an interview.

---

## Rules for our learning sessions

1. **One task at a time.** We won't jump to the next task until the current one works or we understand what remains.
2. **Type the code yourself.** Looking up syntax is allowed; blindly copying a complete solution is not the goal.
3. **Debug before giving up.** Read the error, identify the line, form a hypothesis, and test it.
4. **Ask questions freely.** No need to pretend you remember syntax or concepts.
5. **Keep the scope small.** We will build the simplest working version first, then improve it.
6. **Track progress here.** After each task, note what you completed, what confused you, and any remaining issue.

## Start here: Task 1

1. Check that Python is installed by running `python --version` or `python3 --version` in your terminal.
2. Create a folder named `ai-expense-tracker`.
3. Inside it, create a file named `main.py`.
4. Write a tiny script that prints `My AI Expense Tracker has started!`.
5. Run it and confirm the message appears.

Don't worry about FastAPI, databases, or AI yet. We'll add those when you're ready.

