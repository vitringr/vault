---
context:
  - "[[C (Programming Language)]]"
  - "[[Function (Programming)]]"
---

# C Functions

Functions in the C programming language.

---

Functions encapsulate reusable logic.

See [[C Scope]]

## Components

The components of a C function:

- **Return Type**: Data type of the returned value, or `void` if nothing is returned.
- **Name**: Identifier for calling the function.
- **Parameters**: Optional input arguments with their data type and name.
- **Body**: Code executed when the function is called.
- **Return**: Uses `return` to exit the function and send value back to the caller.

## Declaration & Definition

To declare a function:

```c
int add(int a, int b);
```

To define a function:

```c
int add(int a, int b) {
  return a + b;
}
```

## Parameter Passing

Parameters can be passed by value (by default), or by reference (using pointers).

### Value

```c
int increase(int x) {
    return ++x;
}
```

This copies the argument. Original variable remains unchanged.

### Reference

```c
int increase(int *x) {
  return ++(*x);
}
```

This passes memory address. Original variable can be modified.
