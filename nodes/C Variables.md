---
context:
  - "[[C (Programming Language)]]"
  - "[[Variable (Programming)]]"
---

#wip

# C Variables

Variables in the C programming language.

---

See [[C Data Types]]

## Definition

```c
int num;      // Declaration
int num = 42; // Initialization
```

## Naming Rules

- Can contain letters, digits, and underscores.
- Must start with a letter or underscore "`_`".
- First `31` characters of names are significant.
- Cannot use [[C Keywords]].
- Case-sensitive.

## Storage

| Keyword    | Lifetime | Scope         | Default Value     |
| ---------- | -------- | ------------- | ----------------- |
| `auto`     | Function | Block         | Garbage           |
| `register` | Function | Block         | Garbage           |
| `extern`   | Program  | Global        | Defined elsewhere |
| `static`   | Program  | File/Function | `0`               |

See [[C Static]]

## Constants

Use `const` to make a variable read-only.

## Scope

See [[C Scope]]

#wip

automatic, register, static, external
