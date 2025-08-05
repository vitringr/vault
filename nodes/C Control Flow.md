---
tags:
  - "data"
context:
  - "[[C (Programming Language)]]"
  - "[[Control Flow]]"
---

# C Control Flow

Control flow in the C programming language.

---

## Conditional Statements

```c
if (condition) {
    // Executes if true
} else if (condition2) {
    // Alternative check
} else {
    // Default case
}
```

```c
result = (condition) ? value_if_true : value_if_false;
```

```c
switch (expression) {
    case constant1:
        // Code
        break;
    case constant2:
        // Code
        break;
    default:
        // Default case
}
```

`switch` works with `int`, `char`, and `enum` types.
`breaks` prevents fall-through to the next case.
`default` is optional but recommended.

## Loops

```c
while (condition) {
    // Repeats while condition is true
}
```

```c
do {
    // Executes at least once
} while (condition);
```

```c
for (initialization; condition; increment) {
    // Controlled iteration
}
```

```c
for (int i = 0; i < 10; i++) {
    for (int j = 0; j < 5; j++) {
        // Inner loop
    }
}
```

`break` exits the loop immediately.
`continue` skips to next iteration.

## Jump Statements

```c
goto label;
// ...
label:
    // Code
```

```c
return expression;  // Exits function
```

`goto` should be used sparingly.
`return` for early exit.
