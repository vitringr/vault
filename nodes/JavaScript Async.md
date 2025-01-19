---
aliases:
  - Asynchronous JavaScript
context:
  - "[[JavaScript]]"
---

# JavaScript Async

Asynchronous programming allows JavaScript to start a potentially long-running task and still be able to be responsive to other events while that task runs.

---

## Event Loop

The event loop in JavaScript is a mechanism that handles and coordinates the execution of code.

It manages asynchronous tasks and events, ensuring non-blocking behavior by processing the _call stack_, _callback queue_, and _microtask queue_ in a prioritized manner.

## Timeout Functions

**`setTimeout()`**: Executes a function after the specified period expires.

**`setInterval()`**: Repeatedly executes a function after a fixed delay. Returns a unique interval ID which can later be used by the `clearInterval()` function, which stops further repeated execution of the function.

Times are declared in milliseconds.

## Callbacks

A callback function is a function passed into another function as an argument.

**Callback Hell**: a headache when too many callbacks are nested one after another, visually looking like a pyramid shape in the code.

## Promises

Promises provide a structured way to handle asynchronous tasks and their results.

They are objects representing the eventual completion or failure of an asynchronous operation.

States:

1. **Pending**: initial state, not yet resolved or rejected.
2. **Fulfilled**: Operation completed successfully.
3. **Rejected**: Operation failed.

Methods:

- **`.then()`**: Handles fullfillment.
- **`catch()`**: Handles rejection.
- **`.finally()`**: Executes after resolution or rejection.

## Async and Await

The `async` and `await` keywords are special syntax to work with Promises more easily and intuitively.

- **`async`**: Declares a function as asynchronous, automatically returning a Promise.
- **`await`**: Pauses execution until the Promise resolves or rejects, resuming with the resolved value or throwing the rejection.
