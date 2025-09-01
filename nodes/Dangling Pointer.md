---
context:
  - "[[Pointer]]"
  - "[[Computer Science]]"
  - "[[Computer Memory]]"
---

# Dangling Pointer

[[Pointer]] that points to a memory location that has been freed or deallocated.

---

The pointer itself still holds the address of the now-invalid memory. Using it leads to undefined and often dangerous behavior.

## Common Causes

There are three primary scenarios that create dangling pointers.

**Deallocation of Memory**: The most common cause. When memory is manually freed, but the poitner is not reset to `NULL`, it becomes dangling.

```c
int main() {
  int *ptr = (int *)malloc(sizeof(int));
  *ptr = 42;

  free(ptr);

  *ptr = 10;        // DANGER!
  int value = *ptr; // DANGER!
}
```

**Function Local Variables**: When a function returns, its local variables are destroyed (the stack frame is popped). A pointer that holds the address of a local variable from another function becomes dangling.

```c
int *createInt() {
  int localVar = 42;
  return &localVar; // DANGER!
}

int main() {
  int *danglingPtr = createInt();
  printf("HELLO");
  printf("Danger: %d\n", *danglingPtr);
  return 0;
}
```

**Multiple Pointers to the Same Memory**: When having two pointers pointing to the same block of memory, freeing memory through one pointer makes the other poitner dangle.

```c
int main() {
  int value = 42;

  int *pa = &value;
  int *pb = &value;

  free(pa);
  pa = NULL;

  printf("%d", *pb); // DANGER!
}
```

## Dangers and Consequences

Using a dangling poitner leads to undefined behavior.

**Might Work by Accident**: The OS might not immediately reclaim the memory, and the old value might still be there. This is the most insidious case as the bug hides itself until it doesn't.

**Might Crash Immediately**: The program might do [[Segmentation Fault]] when trying to access protected or reallocated memory.

**Might Corrupt Data**: The memory may already be assigned to serve another purpose. Writing through the dangling pointer corrupts that new data.

**Security Vulenrability**: Attackers can potentially export dangling pointers to execute arbitrary code.

## Prevention

Prevention is key.

- Set pointers to `NULL` after freeing.
- Avoid returning local stack variable pointers.
- Be careful with multiple pointers.
