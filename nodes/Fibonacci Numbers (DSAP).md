---
context:
  - "[[DSAP]]"
---

# Fibonacci Numbers (DSAP)

Output the first `n` [[Fibonacci Sequence]] numbers.

---

## Solution

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
