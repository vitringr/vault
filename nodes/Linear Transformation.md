---
aliases:
  - Linear Map
context:
  - "[[Morphism]]"
  - "[[Linear Algebra]]"
---

# Linear Transformation

(Linear Map)

[[Morphism]] of a [[Vector Space]] into another.

---

Formally, it is a [[Function (Mathematics)|Function]] that preserves [[Vector]] addition and [[Scalar]] multiplication.

**Function**: Takes a [[Vector]] as input, and returns a vector as output, while respecting the underlying core structure of the vector space.

**Geometric Interpretation**: In [[Geometry]], linear transformations often correspond to operations such as _rotation_, _scaling_, _reflection_, _shearing_, _projection_, or any combination between them.

See [[Linear Transformation Matrix Intuition]]

See [[Common 2D Linear Transformations]]

## Properties

_In general, grid lines remain parallel and evenly spaced, and the origin remains the same._

**Preserved Origin**: Linear transformations must preserve the zero vector (`<0, 0>`) as zero vector.

**Lines Remain Lines**: Straight lines must not be curved after the map. They need to remain straight.

These properties ensure that even after a linear transformation, points in space will continue to preserve some relative position between eachother.

## Basis Vectors

Linear transformations are completely defined by how they affect the [[Basis Vectors]] of a space.

Every vector in the space can be described as a scaling of the basis vectors. The `<x, y>` notation of a vector can be interpreted as `<xi, jy>`, where `i` and `j` are the basis vectors of the space.

Since all vectors are dependent on the basis vectors, changes in the basis vectors reflect on the entire [[Coordinate System]].

## Matrix

Every linear transformation can be represented by a [[Matrix]].

The matrix is a concise way to describe a linear transformation.

It simply records the new positions of the basis vectors `i` and `j`, where:

- The **first column** equals the first basis vector `i`.
- The **second column** equals the second basis vector `j`.

```
┌────┬────┐
│ ix │ jx │
├────┼────┤
│ iy │ jy │
└────┴────┘
```

## Vector-Matrix Multiplication

For any vector `<x, y>`, and any matrix `[a, b, c, d]`:

- The `x` component of the vector scales the `i` basis vector column `a, c`.
- The `y` component of the vector scales the `j` basis vector column `b, d`.

Then, the now scaled vectors `i` (`<xa, xc>`) and `j` (`<yb, yd>`) are added to produce the final vector sum.

```
 ┌───┐   ┌───┬───┐       ┌───┐       ┌───┐
 │ x │   │ a │ b │       │ a │       │ b │
 ├───┤ * ├───┼───┤ = x * ├───┤ + y * ├───┤ = <xa, xc> + <yb, yd>
 │ y │   │ c │ d │       │ c │       │ d │
 └───┘   └───┴───┘       └───┘       └───┘
```

See [[Matrix Multiplication]]
