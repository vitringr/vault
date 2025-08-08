---
context:
  - "[[Computer Science]]"
  - "[[Mathematics]]"
---

# Asymptotic Analysis

Method that evaluates the [[Computational Complexity]] growth rate of an [[Algorithm]].

---

Describes the growth of [[Time Complexity]] or [[Space Complexity]] of an algorithm as its input increases.

Ignores constants and lower-order terms.

## Notation

| Notation  | Increase        |
| --------- | --------------- |
| `1`       | None (Constant) |
| `log n`   | Logarithmic     |
| `n`       | Linear          |
| `n log n` | Linearithmic    |
| `n²`      | Quadratic       |
| `n³`      | Cubic           |
| `2ⁿ`      | Exponential     |
| `n!`      | Factorial       |

**Worst-case**: See [[Big O Notation]]
**Best-case**: See [[Big Omega Notation]]

## Limitations

**Approximation**: Doesn't account for small inputs, where constants may dominate.

**Growth Only**: Doesn't measure actual runtime, only growth rate.
