---
context:
  - "[[Memory Management]]"
---

# Call Stack

LIFO [[Stack]] that tracks active function calls in a [[Computer Program]].

---

Fast, automatic, CPU-managed, function-scoped memory.

1. **Push**: When a function is called, its stack frame is pushed onto the stack.
2. **Pop**: When the function returns, its frame is popped and memory freed.

**No Fragmentation**: The nature of the stack prevents memory fragmentation as it allocates and deallocates memory contiguously without leaving gaps any inbetween.

## Risks

**Stack Overflow**: If the stack grows too large, often due to infinite [[Recursion]].

```c
void overflow() {
  overflow();
}
```

**Use-After-Return**: Returning a [[Pointer]] to a local variable which gets destroyed.

```c
int* danger() {
  int x = 42;
  return &x;
}
```

**Stack Corruption**: Writing outside of [[Array]] bounds.

```c
void corruption() {
  int arr[3] = {1, 2, 3};
  arr[5] = 42;
}
```
