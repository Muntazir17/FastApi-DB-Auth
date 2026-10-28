# Phase 1 — Python Fundamentals
## AI-Powered Expense Tracker: Learning Checklist

**Project:** AI-Powered Expense Tracker  
**Language:** Python  
**Level:** Beginner / Refreshing fundamentals  
**Learning approach:** Learn → Practise → Build → Review  
**Starting point:** Task 1 completed

### Phase 1 objective

Refresh Python fundamentals by building toward a working command-line expense tracker. Every concept should be practised in the context of the project wherever possible.

### Ground rules

- Complete tasks in order. Don't skip ahead.
- Write the code yourself instead of blindly copying complete solutions.
- Use documentation when needed; looking up syntax is encouraged.
- Debug errors before asking for a complete solution.
- Ask for a review after each task.
- Do not move forward until the current task's completion criteria are met.
- Keep the project simple. No FastAPI, database, or AI integration during this phase.

---

# Task 1 — Project Setup and First Python Script

**Status: COMPLETED**

### Objectives
- [x] Verify that Python is installed.
- [x] Create the `ai-expense-tracker` project folder.
- [x] Create `main.py`.
- [x] Write and run a simple Python script.

### Expected code

```python
print("My AI Expense Tracker has started!")
```

### Completion criteria
- [x] Python runs successfully.
- [x] The script executes without errors.
- [x] The expected message appears in the terminal.

**Deliverable:** A working `main.py` file.

---

# Task 2 — Variables, Data Types, Input, Output and Type Conversion

### Learning objectives

Understand how Python stores information, receives user input, displays results, and converts values between types.

### Topics to learn

- Variables and assignment.
- Naming conventions and meaningful variable names.
- Basic data types: `int`, `float`, `str`, `bool`, and `None`.
- Checking types with `type()`.
- Output using `print()`.
- Input using `input()`.
- Type conversion using `int()`, `float()`, `str()`, and `bool()`.
- Basic arithmetic operators: `+`, `-`, `*`, `/`, `//`, `%`, and `**`.
- Difference between a number and a numeric string.
- Basic variable reassignment.

### Practical exercises

- [ ] Store an expense amount in a variable.
- [ ] Store an expense description and category.
- [ ] Print all three values.
- [ ] Ask the user to enter an expense amount.
- [ ] Convert the entered amount from a string to a number.
- [ ] Calculate the total of two expenses.
- [ ] Display the amount and its Python data type.
- [ ] Experiment with what happens when you add two strings versus two numbers.

### Mini-project exercise

Write a program that asks the user for:
1. Expense description.
2. Expense amount.
3. Expense category.

Then display the information in a readable format.

### Completion criteria

- [ ] Can explain what a variable is.
- [ ] Can identify the basic Python data types.
- [ ] Understands why `input()` returns a string.
- [ ] Can convert numeric input to an integer or float.
- [ ] Can perform basic arithmetic and display the result.

**Deliverable:** A script that accepts expense details and displays them correctly.

---

# Task 3 — Strings, Formatting and String Methods

### Learning objectives

Learn to work with text, format output cleanly, and manipulate user-entered descriptions and categories.

### Topics to learn

- Single, double, and triple-quoted strings.
- String indexing and slicing.
- String immutability.
- String concatenation.
- f-strings and formatted output.
- Common methods: `.strip()`, `.lower()`, `.upper()`, `.title()`, `.capitalize()`, `.replace()`, `.split()`, and `.startswith()`.
- Checking strings with `in`.
- String length using `len()`.
- Escape characters such as `\n` and `\t`.

### Practical exercises

- [ ] Store an expense description containing multiple words.
- [ ] Remove unwanted spaces from user input.
- [ ] Convert category names to lowercase or title case.
- [ ] Replace words inside a string.
- [ ] Extract part of an expense description using slicing.
- [ ] Format an expense using an f-string.
- [ ] Calculate the length of a description.
- [ ] Check whether a description contains a particular word.

### Mini-project exercise

Display an expense as a formatted receipt, including its description, category, and amount.

### Completion criteria

- [ ] Can manipulate strings using common methods.
- [ ] Understands indexing and slicing.
- [ ] Can use f-strings instead of awkward concatenation.
- [ ] Can clean user input before processing it.

**Deliverable:** A formatted expense receipt.

---

# Task 4 — Conditions and Boolean Logic

### Learning objectives

Make the program behave differently depending on user input and expense values.

### Topics to learn

- `if`, `elif`, and `else`.
- Comparison operators: `==`, `!=`, `<`, `>`, `<=`, and `>=`.
- Boolean values: `True` and `False`.
- Logical operators: `and`, `or`, and `not`.
- Truthy and falsy values.
- Membership checks using `in`.
- Nested conditions.
- Combining multiple conditions.

### Practical exercises

- [ ] Check whether an expense exceeds a specified amount.
- [ ] Categorise an expense as small, medium, or large using chosen thresholds.
- [ ] Check whether a category matches an allowed category.
- [ ] Reject an empty description.
- [ ] Check whether an expense amount is positive.
- [ ] Combine two conditions using `and`.
- [ ] Use `or` to accept more than one valid category.
- [ ] Use `not` to reverse a Boolean condition.

### Mini-project exercise

Build an expense checker that:
- Accepts an amount and category.
- Rejects non-positive amounts.
- Displays a message based on the amount.
- Warns the user when the amount exceeds a chosen threshold.

### Completion criteria

- [ ] Can write basic conditional statements.
- [ ] Can compare values correctly.
- [ ] Understands the difference between `and` and `or`.
- [ ] Can implement simple business rules.

**Deliverable:** An expense validation and classification script.

---

# Task 5 — Loops and Iteration

### Learning objectives

Repeat operations without writing the same code multiple times.

### Topics to learn

- `for` loops.
- `while` loops.
- The `range()` function.
- Iterating over strings and collections.
- `break` and `continue`.
- Loop counters and accumulators.
- Nested loops at a basic level.
- Avoiding infinite loops.

### Practical exercises

- [ ] Print a sequence of numbers using `range()`.
- [ ] Repeat a prompt until the user enters a valid choice.
- [ ] Collect several expense amounts.
- [ ] Calculate the total of multiple amounts.
- [ ] Count the number of expenses entered.
- [ ] Skip an invalid or unwanted entry using `continue`.
- [ ] Stop a loop when the user chooses to exit.

### Mini-project exercise

Create a program that accepts multiple expense amounts and calculates the total and number of entries.

### Completion criteria

- [ ] Can choose between a `for` loop and a `while` loop.
- [ ] Can iterate over multiple values.
- [ ] Can accumulate a running total.
- [ ] Can stop a loop safely.

**Deliverable:** A multi-expense total calculator.

---

# Task 6 — Lists, Tuples, Sets and Dictionaries

### Learning objectives

Understand Python's main collection types and select the appropriate structure for storing expense information.

### Topics to learn

**Lists**
- Creating, indexing, slicing, updating and deleting elements.
- Methods: `.append()`, `.extend()`, `.insert()`, `.remove()`, `.pop()`, and `.sort()`.

**Tuples**
- Creating tuples.
- Accessing elements.
- Understanding immutability.

**Sets**
- Removing duplicates.
- Membership checks.
- Basic union and intersection.

**Dictionaries**
- Key-value pairs.
- Accessing and updating values.
- Adding and removing keys.
- Methods: `.get()`, `.keys()`, `.values()`, `.items()`, and `.update()`.

### Practical exercises

- [ ] Store several expense amounts in a list.
- [ ] Add and remove expense entries.
- [ ] Store fixed category choices in a tuple.
- [ ] Use a set to find unique expense categories.
- [ ] Represent one expense using a dictionary.
- [ ] Store multiple expense dictionaries in a list.
- [ ] Retrieve an expense amount using a dictionary key.
- [ ] Calculate a total from a list of expense records.

### Mini-project exercise

Represent expenses in this structure:

```python
expenses = [
    {
        "description": "Lunch",
        "amount": 150.0,
        "category": "Food"
    },
    {
        "description": "Bus ticket",
        "amount": 30.0,
        "category": "Travel"
    }
]
```

Add more entries and calculate the total spending.

### Completion criteria

- [ ] Understands when to use a list, tuple, set, or dictionary.
- [ ] Can access and update collection elements.
- [ ] Can represent a single expense as a dictionary.
- [ ] Can represent multiple expenses as a list of dictionaries.

**Deliverable:** An in-memory collection of expense records.

---

# Task 7 — Functions, Parameters, Return Values, Scope and Defaults

### Learning objectives

Organise code into reusable units instead of writing the entire program in one block.

### Topics to learn

- Defining functions using `def`.
- Calling functions.
- Parameters and arguments.
- Positional and keyword arguments.
- Return values versus `print()`.
- Default parameter values.
- Local and global scope.
- Returning multiple values.
- Basic docstrings.
- Avoiding unnecessary global variables.

### Practical exercises

- [ ] Write a function that displays an expense.
- [ ] Write a function that returns the total of two amounts.
- [ ] Write a function that calculates the total of a list of expenses.
- [ ] Write a function that filters expenses by category.
- [ ] Add a default category parameter.
- [ ] Call functions using both positional and keyword arguments.
- [ ] Demonstrate the difference between returning a value and printing it.
- [ ] Split a long script into smaller functions.

### Mini-project exercise

Create reusable functions for:
- Adding an expense to a collection.
- Displaying an expense.
- Calculating total spending.
- Listing expenses by category.

### Completion criteria

- [ ] Can define and call functions.
- [ ] Understands parameters, arguments and return values.
- [ ] Can reuse a function for multiple inputs.
- [ ] Understands basic variable scope.

**Deliverable:** A function-based expense tracker prototype.

---

# Task 8 — Error Handling and Tracebacks

### Learning objectives

Understand common Python errors, read error messages, and handle expected failures gracefully.

### Topics to learn

- Syntax errors.
- Runtime errors and exceptions.
- Reading tracebacks from the bottom upward.
- `try` and `except`.
- Catching specific exceptions.
- `else` and `finally`.
- Raising exceptions using `raise`.
- Basic input validation.
- Difference between preventing errors and handling errors.

### Practical exercises

- [ ] Trigger and identify a `SyntaxError`.
- [ ] Trigger a `ValueError` by converting invalid text to a number.
- [ ] Handle invalid numeric input using `try` and `except`.
- [ ] Handle a missing dictionary key.
- [ ] Catch only the exception you expect.
- [ ] Use `else` after successful processing.
- [ ] Explain when `finally` runs.
- [ ] Raise an exception when an expense amount is invalid.

### Mini-project exercise

Update the expense input program so invalid amounts do not crash it. Ask the user to try again when appropriate.

### Completion criteria

- [ ] Can read a basic traceback and identify the failing line.
- [ ] Can distinguish common syntax and runtime errors.
- [ ] Can handle invalid numeric input.
- [ ] Avoids silently swallowing every exception.

**Deliverable:** An expense input program with basic error handling.

---

# Task 9 — Files and JSON

### Learning objectives

Store expense data on disk so it survives after the program closes.

### Topics to learn

- Opening files with `open()`.
- File modes: `r`, `w`, and `a`.
- Using `with` to manage files.
- Reading and writing text.
- The `json` module.
- `json.dump()` and `json.load()`.
- `json.dumps()` and `json.loads()`.
- JSON objects, arrays, strings and numbers.
- Handling missing files and malformed JSON.
- Understanding why persistent storage is useful.

### Practical exercises

- [ ] Write text to a file.
- [ ] Read the contents of a file.
- [ ] Append new text without replacing the existing contents.
- [ ] Convert an expense dictionary to JSON.
- [ ] Save a list of expenses to a JSON file.
- [ ] Load saved expenses when the program starts.
- [ ] Add a new expense and save the updated list.
- [ ] Handle the case where the JSON file does not exist.

### Mini-project exercise

Save expense records in `expenses.json` and load them the next time the program runs.

### Completion criteria

- [ ] Can read and write files.
- [ ] Understands basic JSON conversion.
- [ ] Can save and reload a list of expense dictionaries.
- [ ] Understands the difference between temporary in-memory data and persistent data.

**Deliverable:** An expense tracker that retains data between runs.

---

# Task 10 — Modules, Imports, Virtual Environments and Packages

### Learning objectives

Understand how Python code is organised across files and how project dependencies are managed.

### Topics to learn

- What a module is.
- Importing standard-library modules.
- Creating and importing your own Python modules.
- The difference between a module and a package.
- What `pip` does.
- What a virtual environment does.
- Activating and deactivating a virtual environment.
- Installing and checking packages.
- Understanding `requirements.txt` at a basic level.
- Using `python -m pip` when appropriate.
- Avoiding unnecessary global package installations.

### Practical exercises

- [ ] Import `json` and `datetime`.
- [ ] Move a helper function into a separate Python file.
- [ ] Import that function into `main.py`.
- [ ] Check which Python interpreter is running.
- [ ] Check installed packages.
- [ ] Install one small, appropriate package in the project environment.
- [ ] Record project dependencies in a requirements file.
- [ ] Explain why dependencies should be isolated from system Python.

### Mini-project exercise

Organise the tracker into separate modules, for example:

```text
ai-expense-tracker/
├── main.py
├── expenses.py
├── storage.py
├── expenses.json
└── requirements.txt
```

The exact structure can evolve as the application grows.

### Completion criteria

- [ ] Can import standard-library modules and personal modules.
- [ ] Understands the purpose of a virtual environment.
- [ ] Can install and inspect packages.
- [ ] Can explain how another developer would identify and install the project's dependencies.

**Deliverable:** A small, organised Python project with isolated dependencies.

---

# Task 11 — Comprehensions, Sorting, Filtering and Built-in Functions

### Learning objectives

Process collections efficiently and express common data transformations clearly.

### Topics to learn

- List comprehensions.
- Dictionary comprehensions.
- Set comprehensions.
- `sorted()` versus `.sort()`.
- `key=` in sorting.
- `sum()`, `min()`, `max()`, `len()`, `any()` and `all()`.
- `enumerate()` and `zip()`.
- Filtering with conditions and comprehensions.
- Choosing readable code over unnecessarily clever expressions.

### Practical exercises

- [ ] Extract all expense amounts into a list.
- [ ] Filter expenses above a chosen amount.
- [ ] Filter expenses by category.
- [ ] Sort expenses from highest to lowest amount.
- [ ] Find the largest and smallest expenses.
- [ ] Calculate average spending.
- [ ] Count expenses by category.
- [ ] Use `enumerate()` to display numbered expense records.
- [ ] Use a dictionary comprehension for a simple summary.

### Mini-project exercise

Produce a spending report showing:
- Total number of expenses.
- Total spending.
- Highest and lowest expenses.
- Expenses sorted by amount.
- Spending grouped by category.

### Completion criteria

- [ ] Can filter and transform collections.
- [ ] Can sort records using a chosen field.
- [ ] Can use common built-in functions correctly.
- [ ] Can write comprehensions that remain readable.

**Deliverable:** An expense analysis report.

---

# Task 12 — Classes, Objects and Dataclasses

### Learning objectives

Understand the basic principles of object-oriented programming and recognise when a class is useful.

### Topics to learn

- Classes and objects.
- Attributes and methods.
- The `__init__()` method.
- The `self` parameter.
- Instance attributes versus class attributes.
- Creating and using objects.
- Basic `dataclass` usage.
- Representing structured data with objects.
- When a dictionary is sufficient and when a class is useful.

### Practical exercises

- [ ] Define an `Expense` class.
- [ ] Create an expense object.
- [ ] Store a description, amount and category as attributes.
- [ ] Add a method that displays the expense.
- [ ] Create multiple expense objects.
- [ ] Reimplement the data structure using `@dataclass`.
- [ ] Compare the class, dataclass and dictionary approaches.

### Mini-project exercise

Represent expenses using a dataclass:

```python
from dataclasses import dataclass

@dataclass
class Expense:
    description: str
    amount: float
    category: str
```

Create multiple instances and calculate their total.

### Completion criteria

- [ ] Can explain what a class and object are.
- [ ] Understands attributes, methods and `self`.
- [ ] Can create and use a dataclass.
- [ ] Can explain why structured expense records are useful.

**Deliverable:** An expense model represented with a dataclass.

---

# Task 13 — Build the Command-Line Expense Tracker

### Learning objectives

Combine the Python concepts learned so far into a functional command-line application.

### Required features

- [ ] Display a menu.
- [ ] Add an expense.
- [ ] List all recorded expenses.
- [ ] Calculate total spending.
- [ ] Display expense descriptions, amounts and categories.
- [ ] Allow the user to continue using the menu until they choose to exit.
- [ ] Handle basic invalid menu choices.
- [ ] Use the appropriate data structures and functions.

### Suggested menu

```text
=== AI Expense Tracker ===

1. Add expense
2. List expenses
3. Show total spending
4. Exit

Choose an option:
```

### Suggested development order

1. Display the menu.
2. Implement the exit option.
3. Implement adding an expense.
4. Implement listing expenses.
5. Implement total calculation.
6. Test the menu repeatedly.
7. Fix errors and test different inputs.

### Constraints

- Use Python's standard library.
- Keep expenses in memory initially.
- Do not add FastAPI, a database or an AI API.
- Reuse functions and data structures from earlier tasks.
- Do not worry about making the interface visually attractive.

### Completion criteria

- [ ] The program runs from the terminal.
- [ ] The user can add multiple expenses.
- [ ] All added expenses can be listed.
- [ ] The total is calculated correctly.
- [ ] The menu keeps running until exit is selected.
- [ ] Basic invalid input is handled.

**Deliverable:** A functional command-line expense tracker.

---

# Task 14 — Refactor and Validate the Expense Tracker

### Learning objectives

Improve the structure and reliability of the existing application without changing its core purpose.

### Refactoring objectives

- [ ] Separate menu logic from expense operations.
- [ ] Create clear functions for adding, listing and calculating expenses.
- [ ] Remove unnecessary duplicated code.
- [ ] Use meaningful variable and function names.
- [ ] Keep each function focused on one responsibility.
- [ ] Add docstrings where they improve understanding.
- [ ] Avoid unnecessary global state.

### Input validation objectives

- [ ] Reject empty expense descriptions.
- [ ] Reject invalid numeric amounts.
- [ ] Reject zero or negative amounts.
- [ ] Handle invalid menu selections.
- [ ] Handle empty expense lists.
- [ ] Ensure totals remain correct after multiple additions.
- [ ] Give useful error messages rather than crashing on expected mistakes.

### Testing checklist

- [ ] Add one valid expense.
- [ ] Add several expenses.
- [ ] Try entering text instead of an amount.
- [ ] Try an empty description.
- [ ] Try a zero amount.
- [ ] Try a negative amount.
- [ ] Try an invalid menu option.
- [ ] Request the total before adding any expenses.
- [ ] Verify the total after multiple additions.

### Completion criteria

- [ ] The application still supports all Task 13 features.
- [ ] Code is divided into small, reusable functions.
- [ ] Expected invalid inputs are handled gracefully.
- [ ] The test scenarios above produce the expected results.
- [ ] You can explain how the program works without relying on a tutorial.

**Deliverable:** A cleaner, more reliable command-line expense tracker.

---

# Phase 1 Final Checkpoint

Before starting Phase 2, confirm that you can:

- [ ] Write a Python script from scratch.
- [ ] Work with variables, data types and user input.
- [ ] Manipulate and format strings.
- [ ] Use conditions and loops.
- [ ] Store data in lists and dictionaries.
- [ ] Write reusable functions.
- [ ] Handle common exceptions.
- [ ] Read and write JSON files.
- [ ] Use modules and a virtual environment.
- [ ] Filter, sort and summarise collections.
- [ ] Create basic classes and dataclasses.
- [ ] Build, debug and refactor a command-line application.

## What comes next?

After completing Phase 1, we'll move to **Phase 2 — Git and Project Structure**, covering repository organisation, `.gitignore`, configuration and environment variables. Then we'll begin HTTP and FastAPI.

## Progress tracker

| Task | Topic | Status |
|---|---|---|
| 1 | Project setup and first script | Completed |
| 2 | Variables, types, input and output | Not started |
| 3 | Strings and formatting | Not started |
| 4 | Conditions and Boolean logic | Not started |
| 5 | Loops | Not started |
| 6 | Collections | Not started |
| 7 | Functions | Not started |
| 8 | Error handling | Not started |
| 9 | Files and JSON | Not started |
| 10 | Modules and environments | Not started |
| 11 | Comprehensions and built-ins | Not started |
| 12 | Classes and dataclasses | Not started |
| 13 | Build the expense tracker | Not started |
| 14 | Refactor and validate | Not started |

**Our working agreement:** We tackle one task at a time. For each task, we'll cover the concepts, work through small exercises, build the required deliverable, review your code, and only then move forward.
