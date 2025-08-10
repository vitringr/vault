---
context:
  - "[[C (Programming Language)]]"
  - "[[Scope (Computer Science)]]"
---

# C Scope

Scope in the C programming language.

---

Scope defines the region of a program where things are accessible.

## Scope Types

### Block Scope

(Local Scope)

Variables declared inside a block (`{}`) are only accessible within that block.

They are destroyed when the block exits.

```c
int main() {
  if (1) {
    int x = 10;
    printf("%d", x); // Good
  }

  printf("%d", y); // Error
}
```

### File Scope

(Global Scope)

Variables declared outside all functions have file scope.

They are accessible from their declaration point until the end of the file.

Can be accessed by other files using `extern`.

```c
#include <stdio.h>

int globalVariable = 10; // File scope

void someFunction() {
  int x = globalVariable; // Good
  printf("%d", x);
}

int main() {
  printf("%d", globalVariable); // Good
}
```

### Program Scope

External linkage.

Variables/functions declared with `extern` can be accessed across multiple files.

```c
// file1.c
int globalVariable = 10;
```

```c
// file2.c
extern int globalVariable; // Good
```

## Scope Rules

Local variables take precedence over global variables:

```c
int x = 10; // Global

void someFunction() {
  int x = 20; // Local
  printf("%d", x); // Prints 20
}
```

Nested blocks can have variables with ther same name where inner shadows outer:

```c
for (int i = 0; i < 5; i++) {
  for (int i = 0; i < 5; i++) {
    printf("%d\n", i); // Prints the inner i
  }
}
```

Global variables persist throughout program execution.

Static variables retain their value even after scope exit.

## Lifetime of Variables

| Scope Type       | Lifetime                  |
| ---------------- | ------------------------- |
| Block Scope      | Until block exits         |
| Function Scope   | Entire function execution |
| File Scope       | Entire program execution  |
| Static Variables | Entire program execution  |
| Dynamic (malloc) | Until `free()` is called  |

## Best Practices

- Minimize global variables
- Use `static` for file-local functions/variables.
- Prefer block scope for temporary variables.
- Avoid variable shadowing.
