---
context:
  - "[[C (Programming Language)]]"
  - [[Record]]
---

#wip

# C Structures

Structures (records) in the C programming language.

---

Structures are user-defined data types that combine data items of different kinds.

```c
struct point {
  int x;
  int y;
};
```

## Typedef

See [[C Typedef]]

```c
typedef struct {
  float a;
  float b;
  float c;
} Triangle;

Triangle aer = {4.2, 1.8, 5.6};
```

## Pointers to Members

## Passing Structures to Functions

Structures can be passed to functions and returned by functions.

### Passed by Value

Since structures are passed by value, these two functions are identical:

```c
struct point combinePoints(struct point point, struct point add) {
  struct point result;
  result.x = point.x + add.x;
  result.y = point.y + add.y;
  return result;
}

struct point combinePoints(struct point point, struct point add) {
  point.x += add.x;
  point.y += add.y;
  return point;
}
```

- Both functions receive copies of `point` and `add`, not the originals.
- Any modifications only affect the local copies inside the function.
- The returned value is also a copy, not the original.

**Pass by Reference**: Structures can be passed by reference using [[C Pointers]].
