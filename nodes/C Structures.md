---
context:
  - "[[C (Programming Language)]]"
  - [[Record]]
---

# C Structures

Structures (records) in the C programming language.

---

Structures are user-defined data types that combine data items (called _members_) of different kinds.

```c
struct Point {
  int x;
  int y;
};

struct Point a = {5, 3};
```

**Data Types**: Each member can be of any C data type, including other structures.

**Name Scope**: The structure defines a new scope for its member names. Different structures can reuse member names without conflict.

## Typedef

Structures can be declared using the `typedef` syntax:

```c
typedef struct {
  float a;
  float b;
  float c;
} Triangle;

Triangle aer = {4.2, 1.8, 5.6};
```

This style is useful for documentation and aesthetic purposes.

## Memory

Members are stored sequentially in memory.

Padding may be added between members for alignment.

**Total Size**: Note that due to the padding, the total size in memory isn't necessarily the sum of member sizes.

- Use `sizeof` to get the total size with padding included.

## Access

Members are accessed using the dot (`.`) operator:

```c
struct Point a = {5, 3};
printf("x: %d\n", a.x);
printf("y: %d\n", a.y);
a.x = a.y = 0;
```

## Pointers

See [[C Pointers]]

Creating a pointer to a structure:

```c
struct Point a = {5, 3};
struct Point *pa = &a;
```

Access through pointers can be done by dereferencing (`*`) and the dot (`.`) orperator:

```c
printf("x: %d\n", (*pa).x);
printf("y: %d\n", (*pa).y);
```

Or more conveniently by the arrow (`->`) operator:

```c
printf("x: %d\n", pa->x);
printf("y: %d\n", pa->y);
```

## Passing Structures to Functions

Structures can be passed to functions and returned by functions.

### Passed by Value

Since structures are passed by value, these two functions are identical:

```c
struct Point combinePoints(struct Point point, struct Point add) {
  struct Point result;
  result.x = point.x + add.x;
  result.y = point.y + add.y;
  return result;
}

struct Point combinePoints(struct Point point, struct Point add) {
  point.x += add.x;
  point.y += add.y;
  return point;
}
```

- Both functions receive copies of `point` and `add`, not the originals.
- Any modifications only affect the local copies inside the function.
- The returned value is also a copy, not the original.
