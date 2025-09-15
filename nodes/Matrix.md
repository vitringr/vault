---
aliases:
  - Matrices
context:
  - "[[Mathematics]]"
---

# Matrix

Rectangular grid of numbers arranged into rows and columns.

---

┌───┬───┬───┐  ┌───┬───┐  ┌───┬───┐
│ a │ b │ c │  │ a │ b │  │ a │ b │
├───┼───┼───┤  ├───┼───┤  ├───┼───┤
│ d │ e │ f │  │ c │ d │  │ c │ d │
├───┼───┼───┤  ├───┼───┤  └───┴───┘
│ g │ h │ i │  │ e │ f │
└───┴───┴───┘  └───┴───┘

**Size**: The size of a matrix is defined by how many rows and columns it contains.

**Notation**: It is said that a matrix with `r` rows and `c` colums is a `r × c` matrix. The notation `m₁₂` denotes the element at row `1` and column `2`.

**Dimension**: The _dimension_ of a matrix is given by the number of rows times the number of columns.

## Square Matrix

A matrix with the same number of rows and columns is called _square matrix_.

**Diagonal Elements**: The _diagonal elements_ of a matrix are those elements for which the row and column indices are the same. The other elements are _non-diagonal elements_.

**Diagonal Matrix**: If all non-diagonal elements are zero, then the matrix is a diagonal matrix.

┌───┬───┬───┐
│ 3 │ 0 │ 0 │
├───┼───┼───┤
│ 0 │ 5 │ 0 │
├───┼───┼───┤
│ 0 │ 0 │ 2 │
└───┴───┴───┘

**Identity Matrix**: The _identity matrix_ is a special diagonal matrix with `1`s on the diagonal and `0`s elsewhere.

┌───┬───┬───┐
│ 1 │ 0 │ 0 │
├───┼───┼───┤
│ 0 │ 1 │ 0 │
├───┼───┼───┤
│ 0 │ 0 │ 1 │
└───┴───┴───┘

The identity matrix is special as it is the multiplicative identity element for matrices.
