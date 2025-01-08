---
context:
  - "[[JavaScript]]"
---

# JavaScript Exceptional Handling

Mechanisms for gracefully managing runtime errors in JavaScript.

---

Involves detecting, catching, and responding to exceptions (unexpected conditions).

**Throw Statement**: The `throw` statement throws a user-defined exception. Execution of the current funtion will stop, and control will be passed to the first `catch` block in the call stack. If no `catch` block exist among caller functions, the program will terminate.

**Try, Catch, Finally**: A structure for handling exceptions.

- `try`: Code that might throw an exception.
- `catch`: Code to handle the exception.
- `finally`: Code that executes afterwards, regardless of result.
