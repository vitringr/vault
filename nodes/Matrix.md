---
aliases:
  - Matrices
context:
  - "[[Mathematics]]"
---

# Matrix

Rectangular grid of numbers arranged into rows and columns.

---

┌───┬───┬───┐ ┌───┬───┐ ┌───┬───┐
│ a │ b │ c │ │ a │ b │ │ a │ b │
├───┼───┼───┤ ├───┼───┤ ├───┼───┤
│ d │ e │ f │ │ c │ d │ │ c │ d │
├───┼───┼───┤ ├───┼───┤ └───┴───┘
│ g │ h │ i │ │ e │ f │
└───┴───┴───┘ └───┴───┘

**Size**: The size of a matrix is defined by how many rows and columns it contains.

**Notation**: It is said that a matrix with `r` rows and `c` colums is a `r × c` matrix. The notation `m₁₂` denotes the element at row `1` and column `2`.

**Dimension**: The _dimension_ of a matrix is given by the number of rows times the number of columns.

## Square Matrix

A matrix with the same number of rows and columns is called _square matrix_.

**Linear Transformation**: A square matrix can fully describe a [[Linear Transformation]] by describing the transformed [[Basis Vectors]] of a [[Vector Space]].

## Diagonal

**Diagonal Elements**: The _diagonal elements_ of a matrix are those elements for which the row and column indices are the same. The other elements are _non-diagonal elements_.

**Diagonal Matrix**: Square matrix where all the non-diagonal elements are zero.

┌───┬───┬───┐
│ 3 │ 0 │ 0 │
├───┼───┼───┤
│ 0 │ 5 │ 0 │
├───┼───┼───┤
│ 0 │ 0 │ 2 │
└───┴───┴───┘

## Identity

The _identity matrix_ is a diagonal matrix with `1`s on the diagonal and `0`s elsewhere. The identity matrix is special as it is the multiplicative identity element for matrices.

┌───┬───┬───┐
│ 1 │ 0 │ 0 │
├───┼───┼───┤
│ 0 │ 1 │ 0 │
├───┼───┼───┤
│ 0 │ 0 │ 1 │
└───┴───┴───┘

## Transposition

Given an `r × c` matrix `M`, the _transpose_ of `M`, denoted by `Mᵀ`, is the `c × r` matrix where the columns are formed from the rows of `M`.

┌───┬───┬───┐ ⇒ ┌───┬───┬───┬───┐
│ a │ b │ c │ ⇒ │ a │ d │ g │ j │
├───┼───┼───┤ ⇒ ├───┼───┼───┼───┤
│ d │ e │ f │ ⇒ │ b │ e │ h │ k │
├───┼───┼───┤ ⇒ ├───┼───┼───┼───┤
│ g │ h │ i │ ⇒ │ c │ f │ i │ l │
├───┼───┼───┤ ⇒ └───┴───┴───┴───┘
│ j │ k │ l │ ⇒
└───┴───┴───┘ ⇒

Significant observations:

- Transposing a matrix, and then transposing it again, results in the original matrix.
- Any diagonal matrix is equal to its transpose.

## Inverse

The _inverse_ of a matrix `A` is another matrix, denoted `A⁻¹`, that reverses the effect of the linear transformation represented by `A`.

When multiplied together, they yield the identity matrix `I`, which represents no transformation.

**Formally**: `A * A⁻¹ = A⁻¹ * A = I`

**Condition**: Not every matrix has an inverse. A matrix must be square and have a non-zero [[Determinant]] to be invertible.

**Geometry**: The inverse of a matrix represents the reverse geometric transform.
