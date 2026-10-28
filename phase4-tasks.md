# Phase 4 — Database Persistence
## AI-Powered Expense Tracker: Learning Checklist

**Project:** AI-Powered Expense Tracker  
**Phase:** 4 of the learning roadmap  
**Tasks:** 26–30  
**Prerequisites:** Phase 3 — HTTP and APIs with FastAPI  
**Learning approach:** Learn → Practise → Integrate → Test → Review

---

# Phase 4 Objective

Replace the temporary in-memory storage in the FastAPI application with a real database.

By the end of this phase, the application will store expenses persistently, retrieve them through API endpoints, manage database schema changes safely, and support PostgreSQL.

## Ground Rules

- Complete tasks in order.
- Continue using the existing expense tracker project.
- Understand SQL before relying on an ORM.
- Introduce SQLite first to keep the initial setup simple.
- Use SQLAlchemy to connect Python code to the database.
- Test that data survives application restarts.
- Keep database credentials out of Git.
- Do not introduce authentication or AI features early.

---

# Task 26 — Learn Basic SQL

## Learning objectives

Understand relational databases and learn how to create, read, update, and delete records using SQL.

### Topics to learn

**1. Database fundamentals**
- What a database is and why applications use one.
- What a relational database is.
- What a table, row, and column represent.
- Data types and constraints.
- The relationship between a Python object and a database record.
- How relational databases differ from in-memory Python collections.

**2. Tables and keys**
- Primary keys.
- Unique values.
- `NOT NULL` constraints.
- Default values.
- Why records need identifiers.
- A basic introduction to foreign keys and relationships.

**3. SQL operations**
- `CREATE TABLE` — create a table.
- `INSERT` — add records.
- `SELECT` — retrieve records.
- `WHERE` — filter records.
- `ORDER BY` — sort records.
- `UPDATE` — modify records.
- `DELETE` — remove records.
- `COUNT()`, `SUM()`, `MIN()`, and `MAX()`.
- Basic aggregate queries using `GROUP BY`.

**4. SQL safety**
- Why SQL statements should be parameterised.
- Why user input should not be concatenated into SQL queries.
- Basic transaction concepts.
- The difference between deleting a record and deleting a table.

### Practical exercises

- [ ] Create an SQLite database file.
- [ ] Create an `expenses` table.
- [ ] Add columns for ID, description, amount, category, and date.
- [ ] Define a primary key.
- [ ] Insert several sample expenses.
- [ ] Retrieve all expenses.
- [ ] Retrieve one expense by its ID.
- [ ] Filter expenses by category.
- [ ] Filter expenses by amount.
- [ ] Sort expenses by amount.
- [ ] Update an expense.
- [ ] Delete an expense.
- [ ] Calculate total spending using `SUM()`.
- [ ] Count expenses using `COUNT()`.
- [ ] Experiment with invalid data and database constraints.

### Example table

| Column | Example type | Purpose |
|---|---|---|
| `id` | Integer | Unique expense identifier |
| `description` | Text | Expense description |
| `amount` | Numeric | Expense amount |
| `category` | Text | Spending category |
| `expense_date` | Date | Date of the expense |

These are illustrative types. Exact declarations will depend on the database and model design.

### Example SQL

```sql
CREATE TABLE expenses (
    id INTEGER PRIMARY KEY,
    description TEXT NOT NULL,
    amount REAL NOT NULL,
    category TEXT NOT NULL,
    expense_date DATE NOT NULL
);
```

Insert a record:

```sql
INSERT INTO expenses (
    description, amount, category, expense_date
)
VALUES (
    'Lunch', 150.00, 'Food', '2026-10-28'
);
```

Retrieve records:

```sql
SELECT *
FROM expenses;
```

Calculate total spending:

```sql
SELECT SUM(amount)
FROM expenses;
```

### Mini-project exercise

Create and populate an expense table using SQL directly. Practise the basic operations before integrating the database with FastAPI.

### Completion criteria

- [ ] Can explain tables, rows, columns, and primary keys.
- [ ] Can create a table and insert records.
- [ ] Can query, filter, and sort records.
- [ ] Can update and delete records.
- [ ] Can calculate totals using aggregate functions.
- [ ] Understands basic constraints and parameterised queries.

**Deliverable:** A small SQLite database manipulated using SQL.

---

# Task 27 — Connect FastAPI to SQLite Using SQLAlchemy

## Learning objectives

Connect the existing application to SQLite and represent expense records using SQLAlchemy models.

### Topics to learn

**1. SQLAlchemy fundamentals**
- What an ORM is.
- Why developers use an ORM.
- The difference between SQLAlchemy and SQL.
- How Python classes map to database tables.
- How Python objects map to database records.
- Understanding SQLAlchemy's modern ORM approach.

**2. Database configuration**
- Creating a database engine.
- Defining a database URL.
- Configuring SQLite connections.
- Understanding database sessions.
- Creating a session for a database operation.
- Closing sessions and releasing resources.
- Understanding why a session should not be shared indiscriminately across requests.

**3. ORM models**
- Defining an expense model.
- Mapping columns to Python attributes.
- Defining primary keys.
- Adding field types and constraints.
- Understanding database defaults and nullable fields.
- Separating API schemas from database models.

**4. Pydantic versus SQLAlchemy**
- Pydantic models validate and describe API data.
- SQLAlchemy models represent database tables and records.
- Why the two models serve different purposes.
- Why an API request schema does not automatically create a database table.

### Practical exercises

- [ ] Install SQLAlchemy in the project environment.
- [ ] Install the appropriate SQLite driver if required.
- [ ] Create a database configuration module.
- [ ] Configure the SQLite database URL.
- [ ] Create a SQLAlchemy engine.
- [ ] Create a session factory.
- [ ] Define a declarative base or the equivalent modern SQLAlchemy model setup.
- [ ] Define an `Expense` database model.
- [ ] Map the model to the `expenses` table.
- [ ] Configure the model's primary key and required columns.
- [ ] Create the database tables for initial development.
- [ ] Verify that the database file is created.
- [ ] Open the database and inspect the schema.
- [ ] Test creating and retrieving one record through SQLAlchemy.

### Suggested project structure

```text
ai-expense-tracker/
├── app/
│   ├── __init__.py
│   ├── main.py
│   ├── database.py
│   ├── models.py
│   └── schemas.py
├── expenses.db
├── README.md
├── .gitignore
└── requirements.txt
```

This is a suggested structure. The exact files may change as the application grows.

The local database file should generally be excluded from Git if it contains development or personal expense data.

### Completion criteria

- [ ] Can explain what an ORM does.
- [ ] Can distinguish API schemas from database models.
- [ ] Can configure a SQLite database connection.
- [ ] Can create and use a SQLAlchemy session.
- [ ] Can map an expense model to a database table.
- [ ] Can insert and retrieve a record using SQLAlchemy.
- [ ] Understands basic session cleanup and resource management.

**Deliverable:** A FastAPI project with a working SQLite connection and SQLAlchemy expense model.

---

# Task 28 — Replace In-Memory Storage With Database Operations

## Learning objectives

Modify the existing API so its endpoints read and write expense records through SQLite rather than storing them in a Python list or dictionary.

### Topics to learn

**1. Database-backed CRUD**
- Creating records using SQLAlchemy.
- Querying records.
- Retrieving records by primary key.
- Updating existing records.
- Deleting records.
- Committing transactions.
- Refreshing ORM objects when generated values are needed.
- Understanding rollback when an operation fails.

**2. FastAPI integration**
- Providing database sessions to endpoints.
- Using FastAPI dependencies for session management.
- Understanding the purpose of `yield` in a session dependency.
- Separating database operations from request validation.
- Handling missing database records.
- Returning validated response models.

**3. Data integrity**
- Ensuring changes are committed.
- Understanding what happens if a transaction fails.
- Avoiding duplicate or inconsistent records.
- Handling concurrent requests at a basic level.
- Understanding why application state should not depend on a single Python list.

### Practical exercises

- [ ] Replace the in-memory expense collection with database-backed storage.
- [ ] Update `POST /expenses` to insert a database record.
- [ ] Update `GET /expenses` to query the database.
- [ ] Update `GET /expenses/{expense_id}` to retrieve a record.
- [ ] Update `PUT /expenses/{expense_id}` to modify a record.
- [ ] Update `PATCH /expenses/{expense_id}` to modify selected fields.
- [ ] Update `DELETE /expenses/{expense_id}` to delete a record.
- [ ] Ensure database sessions are managed correctly.
- [ ] Ensure successful writes are committed.
- [ ] Handle missing records consistently.
- [ ] Test the endpoints through Swagger UI.
- [ ] Restart the server and verify that the records remain available.
- [ ] Confirm that the database file is not accidentally committed to Git.

### Mini-project exercise

Create several expenses through the API, stop the application, restart it, and retrieve the same expenses.

The data should remain available because it is stored in SQLite rather than only in application memory.

### Completion criteria

- [ ] All existing CRUD endpoints use SQLite.
- [ ] No endpoint relies on an in-memory list as its primary data store.
- [ ] Database sessions are properly managed.
- [ ] Changes persist after restarting the application.
- [ ] Missing records return consistent responses.
- [ ] Filtering and pagination continue to work.
- [ ] The API's existing validation and status-code behaviour remains correct.

**Deliverable:** A fully database-backed expense API using SQLite.

---

# Task 29 — Database Migrations and Safe Schema Changes

## Learning objectives

Understand how to change a database schema over time without relying on manually recreating tables or losing existing records.

### Topics to learn

**1. Schema changes**
- What a database schema is.
- Why applications need schema changes.
- Adding, removing, or modifying columns.
- Understanding the risks of destructive changes.
- Why production databases should not be casually recreated.

**2. Database migrations**
- What a migration is.
- Why migrations are version-controlled.
- The purpose of Alembic.
- Migration revision files.
- Upgrade and downgrade operations.
- Migration history and version tracking.
- The difference between model definitions and applied database changes.

**3. Safe migration practices**
- Backing up important data.
- Reviewing generated migration scripts.
- Understanding what a migration will change.
- Testing migrations against a development database.
- Handling non-nullable columns in tables that already contain records.
- Understanding why downgrades are not always lossless.
- Keeping application code and database schema compatible.

### Practical exercises

- [ ] Install Alembic.
- [ ] Initialise Alembic for the project.
- [ ] Configure Alembic to use the SQLite database.
- [ ] Connect Alembic to the SQLAlchemy model metadata.
- [ ] Generate an initial migration.
- [ ] Inspect the migration before applying it.
- [ ] Apply the migration.
- [ ] Inspect the migration history.
- [ ] Add a field to the expense model, such as `notes`.
- [ ] Generate a new migration.
- [ ] Review the migration script.
- [ ] Apply the migration.
- [ ] Verify that the new column exists.
- [ ] Verify that existing expense records remain intact.
- [ ] Practise a safe downgrade in a disposable development database.

### Important distinction

SQLAlchemy models describe the intended database structure. Alembic migrations record and apply changes to an existing database schema.

Changing a model file alone does not automatically update every existing database table.

### Completion criteria

- [ ] Can explain why migrations are needed.
- [ ] Can configure Alembic with SQLAlchemy.
- [ ] Can generate and inspect migration scripts.
- [ ] Can apply a migration and verify the schema.
- [ ] Can explain upgrade and downgrade operations.
- [ ] Understands how to protect existing data during schema changes.

**Deliverable:** A SQLite database managed through version-controlled Alembic migrations.

---

# Task 30 — Configure PostgreSQL and Verify Compatibility

## Learning objectives

Move from a local SQLite database to PostgreSQL while keeping the application architecture and API behaviour consistent.

### Topics to learn

**1. PostgreSQL fundamentals**
- What PostgreSQL is.
- How a database server differs from a local SQLite database file.
- Databases, schemas, tables, and roles.
- Database users and permissions.
- Connection strings and connection URLs.
- Basic PostgreSQL administration.

**2. Connecting Python to PostgreSQL**
- Installing a suitable PostgreSQL driver.
- Configuring the database URL.
- Connecting SQLAlchemy to PostgreSQL.
- Managing credentials through environment variables.
- Understanding connection failures and authentication errors.
- Using separate development and production configuration.

**3. SQLite versus PostgreSQL**
- Embedded database versus database server.
- Differences in data types and SQL behaviour.
- Concurrency and connection handling.
- Differences in deployment and operations.
- Why code that works with one database may require adjustments for another.

**4. Migration compatibility**
- Configuring Alembic for PostgreSQL.
- Applying migrations to a new database.
- Verifying that the database schema matches the models.
- Understanding that migration scripts may require review for database-specific features.

### Practical exercises

- [ ] Install PostgreSQL locally or start it using an appropriate container.
- [ ] Create a dedicated development database.
- [ ] Create or configure a database user with appropriate permissions.
- [ ] Install a suitable Python PostgreSQL driver.
- [ ] Configure the PostgreSQL URL using environment variables.
- [ ] Ensure the connection URL and credentials are not committed to Git.
- [ ] Configure SQLAlchemy to connect to PostgreSQL.
- [ ] Apply the Alembic migrations to PostgreSQL.
- [ ] Verify that the expense table exists.
- [ ] Create an expense through the API.
- [ ] Retrieve the created expense.
- [ ] Update and delete an expense.
- [ ] Test filtering and pagination.
- [ ] Restart the application and verify that data persists.
- [ ] Run the API's existing checks against PostgreSQL.
- [ ] Document how to configure and run the project with PostgreSQL.

### Configuration example

A PostgreSQL connection URL has a structure similar to:

```text
postgresql+psycopg://USER:PASSWORD@HOST:PORT/DATABASE
```

This is a template, not a real credential. The actual URL should be supplied through environment-based configuration, not hard-coded in the source code.

### Completion criteria

- [ ] PostgreSQL is running and accessible.
- [ ] The application can connect using SQLAlchemy.
- [ ] Database credentials are not committed to Git.
- [ ] Migrations can be applied to PostgreSQL.
- [ ] Expense CRUD endpoints work with PostgreSQL.
- [ ] Filtering and pagination still work.
- [ ] Records survive application restarts.
- [ ] Can explain the key differences between SQLite and PostgreSQL.

**Deliverable:** A working PostgreSQL-backed expense API with migration support.

---

# Phase 4 Final Checkpoint

Before moving to Phase 5, verify the following.

## SQL fundamentals
- [ ] Understands tables, rows, columns, and primary keys.
- [ ] Can write basic SQL queries.
- [ ] Understands inserts, updates, deletes, filters, and aggregates.
- [ ] Understands basic database constraints and parameterised queries.

## SQLAlchemy and SQLite
- [ ] Has a working database connection.
- [ ] Has an expense model mapped to a database table.
- [ ] Uses database sessions appropriately.
- [ ] Has replaced in-memory CRUD operations with database operations.
- [ ] Expenses remain available after application restarts.

## Migrations
- [ ] Understands the purpose of database migrations.
- [ ] Can create and apply Alembic migrations.
- [ ] Can make a schema change without casually recreating the database.
- [ ] Can verify that existing records survive a migration.

## PostgreSQL
- [ ] Can configure a PostgreSQL connection.
- [ ] Uses environment variables for connection configuration.
- [ ] Can apply migrations to PostgreSQL.
- [ ] Can run expense CRUD operations using PostgreSQL.
- [ ] Understands the practical differences between SQLite and PostgreSQL.

## Final deliverable

A FastAPI expense tracker backed by PostgreSQL, with SQLAlchemy models, database sessions, migration support, and persistent CRUD operations.

---

# Progress Tracker

| Task | Topic | Status |
|---|---|---|
| 26 | Basic SQL | Not started |
| 27 | SQLite and SQLAlchemy models | Not started |
| 28 | Replace in-memory storage with database operations | Not started |
| 29 | Alembic migrations | Not started |
| 30 | PostgreSQL configuration and verification | Not started |

## What comes next?

**Phase 5 — Useful Features and Reliability**

We'll improve the application with richer expense fields, spending summaries, automated tests, logging, error handling, security improvements, and authentication.

**Working agreement:** One task at a time. We begin Task 26 only after completing Phase 3, and we move forward when the current task works and you understand it.
