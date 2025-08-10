---
context:
  - "[[C (Programming Language)]]"
---

#wip

# C Pointers

ad

---

A pointer is a variable that stores the memory address of another variable.

Operators:

- `&` reference
- `*` dereference

```c
int main() {
  const int a = 42;

  printf("&a:\t%p\n", &a);      // 0x7fff127804bc
  printf("a:\t%d\n", a);        // 42

  const int *pa = &a;

  printf("\n");
  printf("&pa:\t%p\n", &pa);    // 0x7fff127804c0
  printf("pa:\t%p\n", pa);      // 0x7fff127804bc
  printf("*pa:\t%d\n", *pa);    // 42
}
```

#wip
