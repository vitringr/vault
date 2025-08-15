---
context:
  - "[[C (Programming Language)]]"
  - [[Record]]
---

#wip

# C Structures

Structures (records) in the C programming language.

---

## Pointers to Members

```language

```

## Default Pass by Value

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

Both functions receive copies of `point` and `add`, not the originals.

Any modifications only affect the local copies inside the function.

The returned value is also a copy, not the original.
