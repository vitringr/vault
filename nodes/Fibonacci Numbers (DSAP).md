---
context:
  - "[[DSAP]]"
---

# Fibonacci Numbers (DSAP)

Output the first `n` [[Fibonacci Sequence]] numbers.

---

**Difficulty**: Easy
**Time Complexity**: `O(n)` Linear
**Space Complexity**: `0(1)` Constant

```c
void fibonacci(int count) {
  int a = 0;
  int b = 1;
  int c;

  printf("%d\n%d\n", a, b);

  for (int i = 0; i < count; i++) {
    c = a + b;
    printf("%d\n", c);

    a = b;
    b = c;
  }
}
```
