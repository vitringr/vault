---
context:
  - "[[Linear Algebra]]"
---

# Determinant

Number describing the geometric scaling of a [[Linear Transformation]] [[Matrix]].

---

The determinant is a [[Scalar]] value that describes how much a transformation scales areas in 2D space or volumes in ≥3D space.

- **Determinant > 0**: The transformation preserves the orientation of the space. The number itself is the scaling factor.
- **Determinant < 0**: The transformation reverses the orientation of the space. The absolute value of the number is the scaling factor.
- **Determinant = 0**: The transformation squishes the entire space into a lower dimension.

## Calculation

For any 2x2 matrix:

```
┌───┬───┐
│ a │ b │
├───┼───┤
│ c │ d │
└───┴───┘
```

The determinant is calculated as:

`det = a*d - b*c`
