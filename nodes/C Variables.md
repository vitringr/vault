---
context:
  - "[[C (Programming Language)]]"
  - "[[Variable (Programming)]]"
---

# C Variables

Variables in the C programming language.

---

## Definition and Scope

```c
int num;      // Declaration
int num = 42; // Initialization
```

See [[C Data Types]]
See [[C Scope]]

## Naming Rules

- Can contain letters, digits, and underscores.
- Must start with a letter or underscore "`_`".
- First `31` characters of names are significant.
- Cannot use [[C Keywords]].
- Case-sensitive.

## Storage Classes

| Keyword    | Lifetime | Scope         | Default Value     |
| ---------- | -------- | ------------- | ----------------- |
| `auto`     | Function | Block         | Garbage           |
| `register` | Function | Block         | Garbage           |
| `extern`   | Program  | Global        | Defined elsewhere |
| `static`   | Program  | File/Function | `0`               |

- **Auto**: Explicitly declare automatic (stack-allocated) variables. Redundant (locals are `auto` by default) and almost never written explicitly.
- **Register**: Hint to the compiler that a variable is going to be used heavily. Mostly ignored since advanced compilers usually optimize better than humans.
- **Extern**: Decalre a variable or function defined in another file. Used for sharing globals across files. Functions are `extern` by default.
- **Static**: See [[C Static]]

## Read-only

**Constants**: Use `const` to make a variable read-only.

**Macros**: See [[C Macros]]

## Pointers

See [[C Pointers]]

## Best Practices

Initialize variables to avoid undefined behavior.
Use meaningful names.
Minimize global variables.
Prefer macros or `const` for value that shouldn't change.
Take good care of pointers.
