# Phase 3 — HTTP and APIs with FastAPI
## AI-Powered Expense Tracker: Learning Checklist

**Project:** AI-Powered Expense Tracker  
**Phase:** 3 of the learning roadmap  
**Tasks:** 18–25  
**Prerequisites:** Phase 1 — Python Fundamentals; Phase 2 — Git and Project Structure  
**Learning approach:** Learn → Experiment → Implement → Test → Review

---

# Phase 3 Objective

Learn how applications communicate over HTTP and build a REST API using FastAPI.

By the end of this phase, the expense tracker will expose API endpoints that allow a client to create, retrieve, update, delete, filter, and paginate expenses.

The API will initially use **in-memory storage**. Data may disappear when the application restarts; persistent database storage comes in Phase 4.

## Ground Rules

- Complete tasks in order.
- Continue using the existing expense tracker project.
- Write and understand the code yourself.
- Test endpoints using the automatically generated API documentation.
- Inspect HTTP responses, status codes, and error messages.
- Do not introduce a database, authentication, or AI integration yet.
- Review each task before moving to the next.

---

# Task 18 — Understand HTTP, Client/Server Communication and JSON

## Learning objectives

Understand how a client communicates with a server and how an API receives requests and returns responses.

### Topics to learn

**1. Client-server architecture**
- What a client and server are.
- How a browser or application communicates with a backend.
- The role of an API between a client and a server.
- What a request-response cycle looks like.
- The difference between frontend and backend responsibilities.
- What a server address, hostname, port, and URL represent.

**2. HTTP fundamentals**
- What HTTP is.
- The structure of an HTTP request.
- The structure of an HTTP response.
- HTTP methods: `GET`, `POST`, `PUT`, `PATCH`, and `DELETE`.
- Request headers and response headers.
- Request bodies and response bodies.
- URL paths and query parameters.
- The difference between HTTP and HTTPS.

**3. JSON**
- What JSON is and why APIs commonly use it.
- JSON objects, arrays, strings, numbers, Booleans, and `null`.
- The relationship between Python dictionaries and JSON objects.
- The relationship between Python lists and JSON arrays.
- Valid versus invalid JSON syntax.

**4. Common HTTP status codes**
- `200 OK`
- `201 Created`
- `204 No Content`
- `400 Bad Request`
- `401 Unauthorized`
- `403 Forbidden`
- `404 Not Found`
- `422 Unprocessable Content`
- `500 Internal Server Error`

Understand that status codes communicate the result of an HTTP request. Not every API needs to use every code in every situation.

### Practical exercises

- [ ] Explain what happens when you open a website in a browser.
- [ ] Identify the client and server in a simple application.
- [ ] Identify the HTTP method and path in an example request.
- [ ] Distinguish headers from a request body.
- [ ] Write a valid JSON object representing an expense.
- [ ] Convert a Python dictionary into JSON using `json.dumps()`.
- [ ] Convert JSON into a Python object using `json.loads()`.
- [ ] Explain the purpose of the common HTTP methods.
- [ ] Match common status codes with example scenarios.

### Mini-project exercise

Design a sample request for creating an expense:

```http
POST /expenses
Content-Type: application/json
```

Request body:

```json
{
  "description": "Lunch",
  "amount": 150.0,
  "category": "Food"
}
```

Describe what the server should do and what a successful response might contain.

### Completion criteria

- [ ] Can explain the request-response cycle.
- [ ] Understands HTTP methods, headers, paths, and bodies.
- [ ] Can read and write basic JSON.
- [ ] Can explain common HTTP status codes.
- [ ] Understands why APIs use structured requests and responses.

**Deliverable:** A short set of notes containing an example HTTP request, response, JSON body, and status-code explanations.

---

# Task 19 — Create a FastAPI Application and Run It Locally

## Learning objectives

Create the first API endpoint and understand how a Python application becomes an HTTP server.

### Topics to learn

- What FastAPI is.
- What an API framework provides.
- Installing FastAPI and an ASGI server such as Uvicorn.
- Creating a FastAPI application instance.
- Defining a route using a decorator.
- Understanding path operations.
- Returning Python data from an endpoint.
- Running the application locally.
- Understanding host and port settings.
- Development reload and its purpose.
- Reading startup logs and common errors.

### Practical exercises

- [ ] Activate the project's Python virtual environment.
- [ ] Install FastAPI and Uvicorn into that environment.
- [ ] Create a dedicated API entry point, such as `app/main.py`.
- [ ] Create a FastAPI application instance.
- [ ] Add a simple `GET /` endpoint.
- [ ] Return a JSON-compatible dictionary from the endpoint.
- [ ] Run the development server.
- [ ] Open the endpoint in your browser.
- [ ] Stop and restart the server.
- [ ] Inspect the terminal output when the server starts.

### Example application

```python
from fastapi import FastAPI

app = FastAPI()


@app.get("/")
def root():
    return {"message": "AI Expense Tracker API is running!"}
```

Run the application from the project root:

```bash
uv run uvicorn app.main:app --reload
```

This command assumes that the file is located at `app/main.py` and that `app` is importable as a Python package. We'll establish the exact project structure during this task.

### Completion criteria

- [ ] FastAPI is installed in the project environment.
- [ ] The application starts without errors.
- [ ] The root endpoint responds to a `GET` request.
- [ ] The response contains valid JSON.
- [ ] Can explain what `app = FastAPI()` does.
- [ ] Can explain what the route decorator does.
- [ ] Understands the purpose of Uvicorn.

**Deliverable:** A running FastAPI application with a working root endpoint.

---

# Task 20 — Automatic API Documentation and Test Requests

## Learning objectives

Use FastAPI's automatically generated documentation to explore and test endpoints without needing a separate API client initially.

### Topics to learn

- What API documentation is.
- OpenAPI and its purpose.
- Swagger UI.
- ReDoc.
- How FastAPI generates API documentation.
- How to send requests from Swagger UI.
- How to inspect response bodies and status codes.
- How to identify validation errors.
- The difference between documentation and the actual implementation.

### Practical exercises

- [ ] Open the Swagger UI page at `/docs`.
- [ ] Open the ReDoc page at `/redoc`.
- [ ] Find the root endpoint in Swagger UI.
- [ ] Execute a test request.
- [ ] Inspect the response body.
- [ ] Inspect the response status code.
- [ ] Compare the documented endpoint with the actual Python route.
- [ ] Identify how the API's paths and methods appear in OpenAPI documentation.

### Mini-project exercise

Add a simple endpoint:

```text
GET /health
```

It should return a JSON response indicating that the service is healthy.

For example:

```json
{
  "status": "ok"
}
```

Test both the root and health endpoints in Swagger UI.

### Completion criteria

- [ ] Can open `/docs` and `/redoc`.
- [ ] Can execute an endpoint from Swagger UI.
- [ ] Can inspect request and response details.
- [ ] Understands how FastAPI produces API documentation.
- [ ] Can test a simple endpoint without writing a separate client.

**Deliverable:** A documented API with working root and health endpoints.

---

# Task 21 — Pydantic Request and Response Models

## Learning objectives

Define the expected structure of API data and validate incoming requests before the application processes them.

### Topics to learn

**1. Pydantic fundamentals**
- What Pydantic is.
- Why APIs need data validation.
- Defining models using `BaseModel`.
- Declaring fields and their types.
- Required fields and optional fields.
- Default values.
- Basic constraints on strings and numbers.
- Understanding validation errors.

**2. Request models**
- What a request body is.
- Defining a model for creating an expense.
- Validating descriptions, amounts, and categories.
- Understanding how FastAPI reads JSON request bodies.
- What happens when required fields are missing.
- What happens when supplied values have invalid types.

**3. Response models**
- What a response model does.
- Using `response_model` on a route.
- Controlling the shape of API responses.
- Why predictable response structures are useful.
- Understanding that request and response models may differ.

### Practical exercises

- [ ] Create an `ExpenseCreate` Pydantic model.
- [ ] Define `description`, `amount`, and `category` fields.
- [ ] Make required fields mandatory.
- [ ] Add appropriate string and numeric constraints.
- [ ] Try a valid request body.
- [ ] Try a missing description.
- [ ] Try a string where a number is expected.
- [ ] Try a zero or negative amount.
- [ ] Inspect FastAPI's validation response.
- [ ] Create an `ExpenseResponse` model.
- [ ] Add a response model to an endpoint.
- [ ] Compare the request model with the response model.

### Mini-project exercise

Create a temporary endpoint that accepts an expense request and returns validated expense data.

At this stage, the endpoint does not need to save anything permanently.

### Completion criteria

- [ ] Can define a Pydantic model.
- [ ] Understands required fields and type annotations.
- [ ] Can apply basic validation constraints.
- [ ] Can explain how FastAPI uses Pydantic models.
- [ ] Can define a response model.
- [ ] Can interpret common request validation errors.

**Deliverable:** Validated expense input and a predictable response structure.

---

# Task 22 — Add an Endpoint to Create an Expense

## Learning objectives

Build the first meaningful business endpoint and understand how an API accepts data and modifies application state.

### Topics to learn

- The purpose of a `POST` endpoint.
- Reading a validated request body.
- Creating an expense record.
- Generating a unique identifier for each expense.
- Returning the created resource.
- Choosing an appropriate success status code.
- Separating request data from application-generated data.
- Understanding temporary in-memory storage.
- The difference between accepting data and persisting data.

### Practical exercises

- [ ] Define an in-memory collection for expense records.
- [ ] Decide how the application will generate unique expense IDs.
- [ ] Implement `POST /expenses`.
- [ ] Accept an `ExpenseCreate` request body.
- [ ] Create an expense record from validated data.
- [ ] Add the record to in-memory storage.
- [ ] Return the created expense.
- [ ] Include the generated ID in the response.
- [ ] Return `201 Created` for successful creation.
- [ ] Test creating multiple expenses in Swagger UI.
- [ ] Verify that each expense has a distinct ID.

### Example request

```http
POST /expenses
Content-Type: application/json
```

```json
{
  "description": "Lunch",
  "amount": 150.0,
  "category": "Food"
}
```

A successful response could look like:

```json
{
  "id": 1,
  "description": "Lunch",
  "amount": 150.0,
  "category": "Food"
}
```

The ID and response structure are illustrative. Your implementation should define and consistently use its chosen ID type.

### Completion criteria

- [ ] The endpoint accepts a valid expense.
- [ ] Invalid request data is rejected.
- [ ] Each created expense receives a unique identifier.
- [ ] The created expense is stored in memory.
- [ ] The response contains the created record.
- [ ] Successful creation returns the intended status code.
- [ ] Can explain why the data is temporary.

**Deliverable:** A working `POST /expenses` endpoint.

---

# Task 23 — List, Retrieve, Update and Delete Expenses

## Learning objectives

Implement the main CRUD operations and understand how clients interact with individual resources and collections.

CRUD stands for Create, Read, Update, and Delete.

### Topics to learn

- Collection endpoints versus individual-resource endpoints.
- Retrieving a list of records.
- Retrieving one record using a path parameter.
- Updating an existing record.
- The difference between `PUT` and `PATCH`.
- Deleting a record.
- Identifying records using IDs.
- Handling missing resources.
- Keeping endpoint behaviour consistent.

### Required endpoints

- [ ] `GET /expenses` — list all expenses.
- [ ] `GET /expenses/{expense_id}` — retrieve one expense.
- [ ] `PUT /expenses/{expense_id}` — replace an expense's editable fields.
- [ ] `PATCH /expenses/{expense_id}` — partially update an expense.
- [ ] `DELETE /expenses/{expense_id}` — delete an expense.

The plan includes both `PUT` and `PATCH` so you can understand the distinction. Implement them in manageable steps rather than all at once.

### Practical exercises

- [ ] Return an empty list when there are no expenses.
- [ ] Return all created expenses.
- [ ] Retrieve an expense using its ID.
- [ ] Return a not-found response for an unknown ID.
- [ ] Replace an expense using `PUT`.
- [ ] Update only selected fields using `PATCH`.
- [ ] Delete an existing expense.
- [ ] Verify that a deleted expense no longer appears in the list.
- [ ] Verify that other expenses remain unchanged.
- [ ] Test each endpoint using Swagger UI.

### Completion criteria

- [ ] Can list all expenses.
- [ ] Can retrieve an individual expense.
- [ ] Can update an existing expense.
- [ ] Understands the difference between `PUT` and `PATCH`.
- [ ] Can delete an expense.
- [ ] Missing IDs are handled consistently.
- [ ] The API behaves correctly after a sequence of CRUD operations.

**Deliverable:** A complete set of in-memory expense CRUD endpoints.

---

# Task 24 — Filtering, Query Parameters and Pagination

## Learning objectives

Make the API more useful by allowing clients to request only the expenses they need.

### Topics to learn

**1. Query parameters**
- What query parameters are.
- Difference between path parameters and query parameters.
- Reading query parameters in FastAPI.
- Optional query parameters.
- Default values.
- Validating query parameter values.

**2. Filtering**
- Filtering by category.
- Filtering by minimum and maximum amount.
- Filtering by date.
- Combining multiple filters.
- Handling missing or optional filter values.

**3. Pagination**
- Why returning every record can become inefficient.
- Page numbers and page sizes.
- Offset and limit.
- Validating pagination values.
- Understanding how filtering interacts with pagination.
- Returning consistent list responses.

### Practical exercises

- [ ] Add a category filter to `GET /expenses`.
- [ ] Add a minimum amount filter.
- [ ] Add a maximum amount filter.
- [ ] Add date filtering once expenses have a date field.
- [ ] Combine two or more filters.
- [ ] Add `limit` and `offset` query parameters.
- [ ] Choose sensible default values.
- [ ] Reject negative offsets.
- [ ] Restrict page size to a reasonable maximum.
- [ ] Test filtering with no matching records.
- [ ] Test filtering and pagination together.

### Example requests

```text
GET /expenses?category=Food
```

```text
GET /expenses?min_amount=100&max_amount=500
```

```text
GET /expenses?limit=10&offset=0
```

These are illustrative query patterns. The exact parameter names should match your implementation.

### Date-filtering prerequisite

If the expense model does not yet contain a date field, introduce one as part of this task. Choose a consistent representation and validate incoming dates before comparing them.

### Completion criteria

- [ ] Can define and validate query parameters.
- [ ] Can filter by category.
- [ ] Can filter by amount range.
- [ ] Can filter by date.
- [ ] Can combine filters.
- [ ] Can implement limit/offset pagination.
- [ ] Understands how pagination changes the returned collection.
- [ ] Can test filter combinations through Swagger UI.

**Deliverable:** A list endpoint supporting filtering and pagination.

---

# Task 25 — Status Codes, Error Handling and Consistent API Behaviour

## Learning objectives

Make the API predictable by returning appropriate status codes and useful error responses for both successful and unsuccessful requests.

### Topics to learn

**1. Success responses**
- `200 OK` for successful reads and updates where a response body is returned.
- `201 Created` for successful resource creation.
- `204 No Content` for successful deletion when no response body is returned.

**2. Client errors**
- `400 Bad Request` for applicable malformed or invalid requests.
- `404 Not Found` when a requested expense does not exist.
- `422 Unprocessable Content` for FastAPI request-validation failures.
- Understanding that different errors have different meanings.

**3. Error handling in FastAPI**
- Raising `HTTPException`.
- Setting status codes explicitly when needed.
- Returning meaningful error details.
- Handling missing resources consistently.
- Understanding FastAPI's default validation errors.
- Avoiding exposing internal implementation details.

**4. API consistency**
- Using predictable response structures.
- Choosing the same behaviour for equivalent operations.
- Distinguishing validation failures from missing records.
- Understanding the difference between expected client errors and unexpected server errors.
- Testing both success and failure paths.

### Practical exercises

- [ ] Verify that expense creation returns `201`.
- [ ] Verify that successful reads return `200`.
- [ ] Choose and implement consistent update responses.
- [ ] Return `404` for an unknown expense ID.
- [ ] Confirm that invalid request bodies produce validation errors.
- [ ] Return `204` for successful deletion if the endpoint has no response body.
- [ ] Test deleting a nonexistent expense.
- [ ] Test updating a nonexistent expense.
- [ ] Check that errors include useful messages.
- [ ] Verify that successful endpoints still work after error handling changes.
- [ ] Inspect the final behaviour through Swagger UI.

### Suggested error response

For an expense ID that does not exist, a response might look like:

```json
{
  "detail": "Expense not found"
}
```

FastAPI commonly uses this `detail` format for `HTTPException` responses.

### Completion criteria

- [ ] Success status codes are appropriate.
- [ ] Missing resources consistently return `404`.
- [ ] Invalid request bodies are rejected.
- [ ] Error responses are understandable.
- [ ] The API does not expose unnecessary internal details.
- [ ] CRUD, filtering, and pagination still work.
- [ ] Can explain why status codes matter to API clients.

**Deliverable:** A working API with consistent success and error behaviour.

---

# Phase 3 Final Checkpoint

Before moving to Phase 4, verify the following.

## HTTP and FastAPI fundamentals

- [ ] Understands the client-server request-response cycle.
- [ ] Understands HTTP methods, headers, bodies, and status codes.
- [ ] Can explain JSON request and response data.
- [ ] Can create and run a FastAPI application locally.
- [ ] Can test endpoints using `/docs`.

## Data validation and CRUD

- [ ] Uses Pydantic models for request validation.
- [ ] Has a working endpoint to create expenses.
- [ ] Can list, retrieve, update, and delete expenses.
- [ ] Handles nonexistent expense IDs correctly.
- [ ] Uses appropriate response status codes.

## Filtering and reliability

- [ ] Supports category filtering.
- [ ] Supports amount filtering.
- [ ] Supports date filtering.
- [ ] Supports pagination.
- [ ] Returns consistent error responses.
- [ ] Has tested both successful and unsuccessful requests.

## Final deliverable

A working FastAPI REST API that manages expenses through HTTP requests, validates input, supports CRUD operations, and provides filtering and pagination.

The API uses temporary in-memory storage at this stage. Restarting the server may reset its data; persistent storage will be introduced in Phase 4.

---

# Progress Tracker

| Task | Topic | Status |
|---|---|---|
| 18 | HTTP, client/server, JSON and status codes | Not started |
| 19 | Create and run a FastAPI application | Not started |
| 20 | Automatic API documentation and test requests | Not started |
| 21 | Pydantic request and response models | Not started |
| 22 | Create an expense endpoint | Not started |
| 23 | List, retrieve, update and delete expenses | Not started |
| 24 | Filtering and pagination | Not started |
| 25 | Status codes and error handling | Not started |

## What comes next?

**Phase 4 — Database Persistence**

We'll learn SQL, connect the application to SQLite, model expenses using SQLAlchemy, replace in-memory storage with database operations, and later introduce PostgreSQL.

**Working agreement:** One task at a time. We start Task 18 only after completing Phase 2, and we move forward only when the current task works and you understand it.
