---
context:
  - "[[C (Programming Language)]]"
---

# C Typedef

Typedefs in the C programming language.

---

The `typedef` keyword creates an alias for existing [[C Data Types]].

Useful for better readability, abstraction, and aesthetics.

```c
typedef int Length;
Length a = 42;
```

Commonly used with [[C Structures]]:

```c
typedef struct {
  int x;
  int y;
} Point;

Point a = {5, 3};
```

The name of the structure can also be included:

```c
typedef struct Node {
  struct Node *next;
  int data;
} Node;
```

This is useful for self-referential structures for example, as well as accessing structures with the `struct` keyword if needed.
