---
context:
  - "[[Mathematics]]"
---

# Dot Product

The sum of the products of the corresponding entries of two sequences of numbers.

---

```
A·B = A.x * B.x + A.y * B.y + ... + A.n * B.n
```

**Projection**: The dot product can measure the projection of one vector onto another, multiplied by magnitude.

**Relative Orientation**: The sign of the dot product gives a rough classification of the relative orientation of two vectors.

| A·B   | θ                | Angle  | Orientation                |
| ----- | ---------------- | ------ | -------------------------- |
| `> 0` | `0° < θ < 90°`   | acute  | roughly same direction     |
| `= 0` | `θ = 90°`        | right  | perpendicular              |
| `< 0` | `90° < θ < 180°` | obtuse | roughly opposite direction |

Orientation applies regardless of magnitude, as the magnitudes of the vectors don't affect the sign of the dot product.

**Cosine Relation**: The dot product of two vectors is equal to the cosine of the angle (`θ`) between them, multiplied by the product of their magnitudes.

```
A·B = abs(A) * abs(B) * cos(θ)

cos(θ) = (A·B) / (abs(A) * abs(B))
```
