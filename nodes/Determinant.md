---
context:
  - "[[Linear Algebra]]"
---

# Determinant

[[Scalar]] number describing the geometric scaling of a [[Linear Transformation]] [[Matrix]].

---

The determinant describes how much a linear transformation scales areas in 2D space or volumes in ≥3D space.

- **Determinant > `0`**: The transformation preserves the orientation of the space. The number itself is the scaling factor.
- **Determinant < `0`**: The transformation reverses the orientation of the space. The absolute value of the number is the scaling factor.
- **Determinant = `0`**: The transformation squishes the entire space into a lower dimension.

## Calculation

For any 2x2 matrix:

┌───┬───┐
│ a │ b │
├───┼───┤
│ c │ d │
└───┴───┘

The determinant is calculated as: `det = a*d - b*c`

## Properties

The determinant of an identity matrix of any dimension is `1`.

The determinant of a matrix product is equal to the product of the determinants.

The determinant of the transpose of a matrix is equal to the original determinant.

If any row or column in a matrix contains all zeroes, then the determinant of that matrix is `0`.

A matrix is invertible only if its determinant is not zero.
