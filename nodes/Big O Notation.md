---
aliases:
  - Big O
context:
  - "[[Computational Complexity]]"
---

# Big O Notation

Describes the growth of [[Computational Complexity]] of an [[Algorithm]] as its input size increases.

---

Approximates the increase of [[Time Complexity]] or [[Space Complexity]] of an algorithm, scaling with input size.

**Notation**: `O(n)`, where `n` is the increasing input.

Ignores constants and lower-order terms.

Focuses on the worst-case scenario.

## Common Complexities

| Notation     | Increase        |
| ------------ | --------------- |
| `O(1)`       | None (Constant) |
| `O(log n)`   | Logarithmic     |
| `O(n)`       | Linear          |
| `O(n log n)` | Linearithmic    |
| `O(n²)`      | Polynomial      |
| `O(2ⁿ)`      | Exponential     |
| `O(n!)`      | Factorial       |
