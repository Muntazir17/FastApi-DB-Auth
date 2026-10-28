# Phase 5 — Features, Reliability and AI Integration
## AI-Powered Expense Tracker: Learning Checklist

**Project:** AI-Powered Expense Tracker  
**Phase:** 5 of the learning roadmap  
**Tasks:** 31–38  
**Prerequisites:** Phase 4 — Database Persistence  
**Learning approach:** Learn → Implement → Test → Integrate → Review

---

# Phase 5 Objective

Turn the database-backed expense API into a useful, reliable application with expense analytics, automated tests, authentication, and an AI-powered spending-insights feature.

We'll build the core functionality first, make it reliable and secure, and then integrate an external AI API.

By the end of this phase, users will be able to manage their expenses, review their spending patterns, securely access their own data, and ask an AI assistant questions about their spending.

## Ground Rules

- Complete tasks in order.
- Continue building on the existing FastAPI and PostgreSQL application.
- Test features before adding more complexity.
- Keep AI-generated insights separate from authoritative financial calculations.
- Never expose API keys or passwords in source code.
- Send only the expense information needed for a particular AI request.
- Do not begin Docker or deployment until this phase is complete.

---

# Task 31 — Improve Expense Fields and Validation

## Learning objectives

Make expense records more useful by adding appropriate fields and enforcing consistent validation rules.

### Topics to learn

**1. Expense data modelling**
- Description and amount.
- Category.
- Expense date.
- Optional notes.
- Created and updated timestamps.
- Required versus optional fields.
- Database constraints versus API validation.

**2. Validation**
- Validating numeric amounts.
- Rejecting zero or negative expenses where appropriate.
- Handling empty descriptions.
- Validating date formats.
- Normalising category names.
- Setting reasonable limits on text fields.
- Understanding the difference between Pydantic validation and database constraints.

**3. Updating existing records**
- Updating SQLAlchemy models.
- Updating Pydantic request and response schemas.
- Creating database migrations for new columns.
- Preserving existing expense records.

### Practical exercises

- [ ] Review the current expense model.
- [ ] Add or refine the expense date field.
- [ ] Add an optional notes field if useful.
- [ ] Add creation and update timestamps where appropriate.
- [ ] Define validation rules for amounts and descriptions.
- [ ] Normalise category input consistently.
- [ ] Update request and response models.
- [ ] Generate and apply the required database migration.
- [ ] Verify that existing records remain intact.
- [ ] Test valid and invalid requests.

### Completion criteria

- [ ] Expense records contain the fields the application needs.
- [ ] Invalid expense data is rejected consistently.
- [ ] Database migrations preserve existing data.
- [ ] CRUD endpoints continue working after the schema changes.

**Deliverable:** A better-defined expense model with consistent validation.

---

# Task 32 — Build Spending Summary and Analytics Endpoints

## Learning objectives

Use stored expense data to calculate meaningful summaries and trends.

### Topics to learn

- SQL aggregate functions.
- Grouping records by category.
- Grouping records by month.
- Date ranges and date filtering.
- Calculating totals and averages.
- Difference between aggregating in SQL and processing records in Python.
- Designing predictable API response schemas.
- Handling empty datasets.

### Required features

- [ ] Total spending across all expenses.
- [ ] Total spending for a selected date range.
- [ ] Spending breakdown by category.
- [ ] Monthly spending summaries.
- [ ] Expense count.
- [ ] Average expense amount.
- [ ] Highest and lowest expense.
- [ ] Appropriate filters for summary endpoints.

### Suggested endpoints

```text
GET /expenses/summary
GET /expenses/summary/categories
GET /expenses/summary/monthly
```

These paths are suggestions; use a consistent structure that fits the existing application.

### Practical exercises

- [ ] Calculate total spending using SQL.
- [ ] Group expenses by category.
- [ ] Calculate monthly totals.
- [ ] Support optional date-range parameters.
- [ ] Define Pydantic response models for summaries.
- [ ] Test summaries when the database is empty.
- [ ] Compare API totals against manually calculated totals.
- [ ] Check that filtering and aggregation produce correct results.

### Completion criteria

- [ ] Summary endpoints return correct calculations.
- [ ] Category and monthly breakdowns work.
- [ ] Date filters behave consistently.
- [ ] Empty datasets do not cause errors.
- [ ] Summary calculations can be independently verified.

**Deliverable:** Working expense analytics endpoints.

---

# Task 33 — Automated Testing with pytest

## Learning objectives

Learn to verify application behaviour automatically instead of relying entirely on manual testing.

### Topics to learn

**1. Testing fundamentals**
- What automated testing is.
- Unit tests versus integration tests.
- Test cases, assertions and expected results.
- Test isolation.
- Fixtures in pytest.
- Arrange, Act, Assert.

**2. Testing FastAPI**
- FastAPI's test client.
- Testing HTTP methods and status codes.
- Testing request and response bodies.
- Testing validation failures.
- Testing missing resources.
- Testing database-backed endpoints.

**3. Database testing**
- Using a separate test database.
- Preventing tests from modifying development data.
- Setting up and cleaning up test records.
- Understanding test isolation and repeatability.

### Practical exercises

- [ ] Install pytest and the required test dependencies.
- [ ] Create a `tests/` directory.
- [ ] Test basic expense-related functions.
- [ ] Test successful expense creation.
- [ ] Test retrieving an expense.
- [ ] Test updating and deleting expenses.
- [ ] Test invalid request bodies.
- [ ] Test missing expense IDs.
- [ ] Test filtering and pagination.
- [ ] Test summary calculations.
- [ ] Configure tests to use a separate database.
- [ ] Run the complete test suite repeatedly.

### Suggested structure

```text
tests/
├── conftest.py
├── test_expenses.py
├── test_summary.py
└── test_validation.py
```

### Completion criteria

- [ ] Core functionality has automated tests.
- [ ] Tests cover success and failure cases.
- [ ] Tests do not corrupt development data.
- [ ] The test suite can run from a documented command.
- [ ] Failures identify which behaviour is incorrect.

**Deliverable:** An automated test suite for the expense API.

---

# Task 34 — Error Handling, Logging and Security Improvements

## Learning objectives

Make the application easier to debug and safer to operate.

### Topics to learn

**1. Error handling**
- Expected versus unexpected errors.
- Consistent HTTP error responses.
- Database failure handling.
- Logging exceptions appropriately.
- Avoiding swallowed exceptions.
- Avoiding exposure of internal details in API responses.

**2. Logging**
- Python's `logging` module.
- Log levels: `DEBUG`, `INFO`, `WARNING`, `ERROR`, and `CRITICAL`.
- Logging useful application events.
- Avoiding sensitive data in logs.
- Distinguishing application logs from HTTP responses.

**3. Security fundamentals**
- Input validation.
- SQL injection and parameterised database operations.
- Secrets management.
- Dependency updates.
- Safe error responses.
- Basic rate-limiting concepts.
- Avoiding unnecessary personal data collection.

### Practical exercises

- [ ] Configure structured, consistent application logging.
- [ ] Log important application events.
- [ ] Log unexpected failures without exposing stack traces to API clients.
- [ ] Handle expected database errors appropriately.
- [ ] Review all endpoints for consistent error responses.
- [ ] Verify that secrets are not included in logs.
- [ ] Check that database queries use SQLAlchemy safely.
- [ ] Review environment-variable handling.
- [ ] Test failure cases such as database unavailability.
- [ ] Document how to diagnose common application problems.

### Completion criteria

- [ ] Important application events are logged.
- [ ] Errors are handled consistently.
- [ ] API responses do not expose unnecessary internal details.
- [ ] Sensitive data is not logged unnecessarily.
- [ ] Common failure scenarios have been tested.

**Deliverable:** A more observable, reliable and security-conscious application.

---

# Task 35 — Authentication and User Data Isolation

## Learning objectives

Introduce user accounts and ensure that each user can access only their own expenses.

### Topics to learn

**1. Authentication fundamentals**
- Authentication versus authorisation.
- User registration and login.
- Password hashing.
- Password verification.
- Authentication tokens.
- JWT fundamentals.
- Token expiration and validation.

**2. FastAPI security**
- Security dependencies.
- Protecting endpoints.
- Reading the authenticated user from a request.
- Returning appropriate authentication errors.
- Understanding `401 Unauthorized` versus `403 Forbidden`.

**3. Database design**
- Creating a user model.
- Defining a relationship between users and expenses.
- Adding a user foreign key to expense records.
- Handling existing expenses when introducing user ownership.
- Using migrations to update the schema.

**4. Data isolation**
- Filtering database queries by authenticated user.
- Preventing access to another user's records.
- Protecting summary endpoints.
- Applying ownership checks to updates and deletes.
- Avoiding insecure direct object references.

### Practical exercises

- [ ] Create a user database model.
- [ ] Add a database migration for users and expense ownership.
- [ ] Implement secure password hashing.
- [ ] Add a registration endpoint.
- [ ] Add a login endpoint.
- [ ] Implement token creation and validation.
- [ ] Protect expense endpoints.
- [ ] Associate new expenses with the authenticated user.
- [ ] Restrict list and summary queries to the current user.
- [ ] Prevent users from reading or modifying another user's expenses.
- [ ] Test missing, invalid and expired tokens.
- [ ] Test access using two separate test users.

### Suggested endpoints

```text
POST /auth/register
POST /auth/login
GET  /auth/me
```

These endpoints are examples; their final implementation should match the application's authentication design.

### Completion criteria

- [ ] Users can register and authenticate.
- [ ] Passwords are stored as hashes, not plaintext.
- [ ] Protected endpoints require valid authentication.
- [ ] Each expense is associated with its owner.
- [ ] Users cannot access another user's expense data.
- [ ] Summary endpoints respect user ownership.
- [ ] Authentication failure cases are tested.

**Deliverable:** An authenticated expense API with user-level data isolation.

---

# Task 36 — Learn External API Integration

## Learning objectives

Understand how a backend communicates with an external service and handles network-related failures before introducing an AI feature.

### Topics to learn

**1. External APIs**
- What an external API is.
- Requesting data from another service.
- API endpoints and authentication.
- JSON request and response bodies.
- API keys and bearer tokens.
- Understanding API documentation.

**2. HTTP clients**
- Making requests from Python.
- Using a suitable HTTP client such as HTTPX.
- Timeouts.
- Connection errors.
- HTTP error responses.
- Parsing JSON responses.
- Synchronous versus asynchronous HTTP requests.

**3. Reliability**
- Rate limits.
- Retry behaviour.
- Exponential backoff concepts.
- Handling service unavailability.
- Avoiding infinite retries.
- Understanding request latency and timeouts.

### Practical exercises

- [ ] Choose a simple public test API.
- [ ] Read its API documentation.
- [ ] Make a request from Python.
- [ ] Inspect the response status code and JSON body.
- [ ] Handle unsuccessful HTTP responses.
- [ ] Configure a request timeout.
- [ ] Handle connection and timeout errors.
- [ ] Understand how rate limits are communicated.
- [ ] Implement a bounded retry strategy where appropriate.
- [ ] Keep external service logic separate from expense calculations.

### Mini-project exercise

Create a small service function that calls an external API and returns a predictable result. Test its behaviour when the service fails or responds too slowly.

### Completion criteria

- [ ] Can call an external API from Python.
- [ ] Can parse JSON responses.
- [ ] Understands timeouts and HTTP errors.
- [ ] Can explain rate limiting and bounded retries.
- [ ] Can separate network failures from application logic.

**Deliverable:** A tested external API client suitable for reuse in the AI feature.

---

# Task 37 — Add an AI-Powered Spending Insights Endpoint

## Learning objectives

Integrate a large language model API to generate helpful spending summaries using calculated expense data.

The AI should explain spending patterns, not replace the application's database or financial calculations.

### Topics to learn

**1. LLM API fundamentals**
- What a large language model API provides.
- API requests and responses.
- Model selection and provider documentation.
- System and user instructions.
- Sending structured data as context.
- Understanding response formats.
- Token usage and cost considerations.

**2. AI feature design**
- Separating deterministic calculations from AI-generated commentary.
- Preparing concise spending summaries.
- Designing prompts around a specific user question.
- Avoiding unsupported claims.
- Handling incomplete data.
- Making the output useful and understandable.

**3. Backend integration**
- Creating a dedicated AI service module.
- Calling the provider from the backend.
- Connecting the service to a FastAPI endpoint.
- Validating user questions.
- Handling provider failures.
- Returning predictable response models.

### Suggested endpoint

```text
POST /ai/spending-insights
```

Example request:

```json
{
  "question": "What are my biggest spending categories this month?"
}
```

The backend should calculate the relevant expense summary, then provide only the necessary summary data to the AI service.

An illustrative response:

```json
{
  "insight": "Food is your largest spending category this month..."
}
```

The actual insight must be generated from the user's real expense data; the example above is not a claim about any user's spending.

### Practical exercises

- [ ] Choose an AI API provider and review its current documentation.
- [ ] Create a dedicated AI service module.
- [ ] Configure a model and request format.
- [ ] Calculate the user's expense summary using trusted application logic.
- [ ] Send the summary and question to the model.
- [ ] Validate the request using Pydantic.
- [ ] Return the generated insight through FastAPI.
- [ ] Test questions about category spending.
- [ ] Test monthly spending review questions.
- [ ] Handle empty expense histories.
- [ ] Handle malformed or unexpected model responses.
- [ ] Keep the AI service separate from database CRUD operations.

### Completion criteria

- [ ] The endpoint accepts a valid question.
- [ ] The application supplies relevant, calculated expense summaries.
- [ ] The model produces an understandable response.
- [ ] Empty or insufficient data is handled gracefully.
- [ ] AI failures do not corrupt expense records.
- [ ] The API returns a predictable response structure.

**Deliverable:** An AI spending-insights endpoint connected to the expense tracker.

---

# Task 38 — Secure AI Integration and Test Failure Cases

## Learning objectives

Make the AI feature safer and more reliable by protecting credentials, minimising data sharing, and handling external service failures.

### Topics to learn

**1. API key security**
- Storing keys in environment variables.
- Keeping local secrets out of Git.
- Using `.env.example` with placeholders.
- Avoiding credentials in logs and error responses.
- Rotating an exposed key.
- Using provider-specific usage and spending limits where available.

**2. Data minimisation and privacy**
- Sending only the data necessary for an insight.
- Using aggregated expense summaries where possible.
- Avoiding unnecessary personal information.
- Understanding what data is sent to the AI provider.
- Reviewing the provider's data handling and retention policies.
- Avoiding the transmission of raw records when summaries are sufficient.

**3. Failure handling**
- Handling connection failures.
- Handling request timeouts.
- Handling rate-limit responses.
- Handling provider server errors.
- Handling invalid or incomplete responses.
- Preventing unbounded retries.
- Returning useful, consistent API errors.

**4. Testing and observability**
- Mocking external AI requests in tests.
- Testing success and failure scenarios.
- Avoiding real API calls in ordinary unit tests.
- Logging operational errors without recording secrets.
- Tracking latency and usage where appropriate.

### Practical exercises

- [ ] Load the AI API key from environment configuration.
- [ ] Verify that the key is not committed to Git.
- [ ] Check that logs and error messages do not reveal the key.
- [ ] Send only the necessary expense summary to the model.
- [ ] Test a successful AI response.
- [ ] Test an invalid API key.
- [ ] Test a timeout.
- [ ] Test a rate-limit response.
- [ ] Test a provider server error.
- [ ] Test malformed model output.
- [ ] Mock the provider in automated tests.
- [ ] Verify that AI failures do not damage or alter stored expenses.
- [ ] Review the provider's privacy and usage settings.
- [ ] Document local AI configuration and safe setup instructions.

### Completion criteria

- [ ] The AI API key is not hard-coded or committed.
- [ ] The application shares only necessary expense information.
- [ ] External service failures are handled predictably.
- [ ] Automated tests cover key failure cases.
- [ ] Sensitive values do not appear in logs.
- [ ] AI insights are presented as generated analysis, not guaranteed financial advice.
- [ ] Users' expense records remain intact if the AI provider fails.

**Deliverable:** A secure, tested AI integration with controlled data sharing and failure handling.

---

# Phase 5 Final Checkpoint

Before moving to Phase 6 — Ship the Project, verify the following.

## Expense features
- [ ] Expense records have appropriate fields and validation.
- [ ] Spending summaries work.
- [ ] Category and monthly analytics are correct.

## Reliability
- [ ] Automated tests cover core functionality.
- [ ] Error handling is consistent.
- [ ] Application logs are useful and do not expose secrets.
- [ ] Database failures and invalid inputs are handled appropriately.

## Authentication
- [ ] Users can register and log in.
- [ ] Passwords are securely hashed.
- [ ] Protected endpoints require authentication.
- [ ] Users can access only their own expense data.

## AI integration
- [ ] The backend can call an external AI API.
- [ ] The AI spending-insights endpoint works.
- [ ] Expense summaries are calculated by application logic.
- [ ] API keys are stored outside source code.
- [ ] Only necessary data is sent to the model.
- [ ] Timeouts, rate limits and provider errors are tested.
- [ ] AI failures do not compromise the core expense application.

## Final deliverable

A database-backed, authenticated expense tracker with spending analytics, automated tests, reliable error handling, and a secure AI spending-insights endpoint.

---

# Progress Tracker

| Task | Topic | Status |
|---|---|---|
| 31 | Expense fields and validation | Not started |
| 32 | Spending summaries and analytics | Not started |
| 33 | Automated testing with pytest | Not started |
| 34 | Error handling, logging and security | Not started |
| 35 | Authentication and user data isolation | Not started |
| 36 | External API fundamentals | Not started |
| 37 | AI spending-insights endpoint | Not started |
| 38 | AI security, privacy and failure testing | Not started |

## What comes next?

**Phase 6 — Ship the Project (Tasks 39–40)**

We'll containerise the application with Docker, document the setup, deploy the API and database, verify the live application, and prepare a demo that you can explain in an interview.

**Working agreement:** One task at a time. Complete each feature, test it, review the implementation, and only then move to the next task.
