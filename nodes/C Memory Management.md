---
context:
  - "[[C (Programming Language)]]"
  - "[[Memory Management]]"
---

# C Memory Management

Memory Management in the C programming language.

---

_Great power requires great responsibility._

See [[Memory Layout]]

## Stack Memory

Automatic [[Call Stack]] memory.

The stack is extremely efficient, automatically managed, and automatically cleaned up.

```c
void something() {
    int x = 10;    // Stack allocation
    char arr[100]; // Stack allocation
}                  // Automatic free
```

## Heap Memory

Manual memory management.

Offers a large amount of dynamic memory with flexible size.

The heap is slower than the stack, requires manual memory allocation, and manual memory cleanup.

Memory management functions:
- `malloc()`: Memory allocation.
- `calloc()`: Contiguous memory allocation.
- `realloc()`: Memory re-allocation.
- `free()`: Memory deallocation.

### Best Practices

#wip
