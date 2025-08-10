---
context:
  - "[[C (Programming Language)]]"
---

# C Macros

Macros are preprocessor directives that perform text substitution before compilation.

---

Text substitution with file-wide scope, no type checking, and no memory allocation.

```c
#define PI 3.14159
#define MAX_RUNS 100
#define SOME_NAME "Rex"
```

## Built-in Macros

C provides built-in macros. Examples include:

| Macro          | Description             | Example Output  |
| -------------- | ----------------------- | --------------- |
| `__FILE__`     | Current filename        | `"main.c"`      |
| `__LINE__`     | Current line number     | `42`            |
| `__DATE__`     | Compilation date string | `"Aug 10 2025"` |
| `__TIME__`     | Compilation time string | `"14:13:02"`    |
| `__FUNCTION__` | Current function name   | `"main"`        |
