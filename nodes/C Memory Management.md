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

```c
int main() {
  int size;

  printf("Enter array size: ");
  scanf("%d", &size);

  int *dynamicArray = (int *)malloc(size * sizeof(int));
  if (dynamicArray == NULL) {
    printf("ERROR: Memory allocation failed!\n");
    return 1;
  }

  for (int i = 0; i < size; i++) {
    dynamicArray[i] = i * 10;
  }

  for (int i = 0; i < size; i++) {
    printf("[%d]: %d\n", i, dynamicArray[i]);
  }

  free(dynamicArray);

  printf("DP: %d", *dynamicArray);
  dynamicArray = NULL;

  return 0;
}
```

### Best Practices

**Always Check for NULL**: Always check the return value of `malloc()`, `calloc()`, and `realloc()`. If they fail, they return `NULL`, and dereferencing a `NULL` pointer causes undefined behavior, usually a crash.

**Always Free**: For every allocation, there must be a corresponding deallocation. This prevents [[Memory Leak]].

**Avoid Use-After-Free**: Once you `free()` a [[Pointer]], do not use it again. Setting it to `NULL` immediately after freeing helps catch these bugs.

**Avoid Double-Free**: Never call `free()` on the same pointer more than once. This can corrupt the heap's internal data structures.

**Free Can Handle NULL**: The standard library's `free()` function is defined to do nothing if passed a `NULL` pointer. This means that checks like `if (ptr) free(ptr);` are redundant.

**Beware of Dangling Pointers**: Pointers that point to freed memory are called "dangling pointers". Dereferencing them is a severe error. Set them to `NULL` immediately after freeing them.

**Calculate Sizes Correctly**: Take the data type size into account when allocating, like `ptr = malloc(n * sizeof(type))`.
