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

**Geometry**: Linear transformations correspond to operations that change space, while perserving linear proportions.

**Function**: Takes a [[Vector]] as input, and returns a vector as output, while respecting the underlying core structure of the vector space.

See [[Primitive Linear Transformations]]

## Properties

Any [[Function (Mathematics)|Function]] `F: V → W` between two vector spaces is a linear transformation if it satisfies these two fundamental properties:

- **Additivity**: Linear transformations preserve vector addition: `F(a + b) = F(a) + F(b)`.
- **Homogeneity**: Linear transformations preserve scalar multiplication: `F(ka) = kF(a)`.

These two properties lead directly to several crucial geometric consequences:

- **No Translation**: Linear transformations never translate (shift) space. This distinguishes them from [[Affine Transformation|Affine Transformations]].
- **Preserved Origin**: As a direct result of having no translation, the zero must map to the zero vector, thus preserving the origin of the space.
- **Lines Remain Lines**: Straight lines are mapped to straight lines (or to the zero vector). They are never curved.
- **Preserved Linear Structure**: [[Linear Combination]] relationships are preserved. If a point can be described as a weighted sum of other points, this relationship holds after the trasnformation.
- **Parallel and Evenly Spaced**: In general, grid lines remain parallel and evenly spaced.

In essence, these properties ensure that the linearity of the vector space is preserved. The relative positions of points are maintained in a linear sense.

## Basis Vectors

Linear transformations are completely defined by how they affect the [[Basis Vectors]] of a space.

Every vector in the space can be described as a scaling of the basis vectors. The `<x, y>` notation of a vector can be interpreted as `<xi, jy>`, where `i` and `j` are the basis vectors of the space.

Since all vectors are dependent on the basis vectors, changes in the basis vectors reflect on the entire [[Coordinate System]].

## Determinant

The determinant is a number that describes how a linear transformation affects the scaling of space.

See [[Determinant]]

## Invertibility

Any transformation `F` is _invertible_ if there exist an opposite transformation `F⁻¹`, known as the _inverse of `F`_, that "undoes" the original transformation.

All [[Primitive Linear Transformations]] other than projection are invertible. Projection is not invertible since it effectively discards a dimension worth of information.

## Matrix

Every linear transformation can be described by a [[Matrix]].

The matrix simply records the new positions of the basis vectors `i` and `j`, where:

- The **first column** equals the first basis vector `i`.
- The **second column** equals the second basis vector `j`.

┌─────┬─────┐
│ i.x │ j.x │
├─────┼─────┤
│ i.y │ j.y │
└─────┴─────┘

For any vector `<u, v>`, and any matrix `[a, b, c, d]`:

- The `u` component of the vector scales the `i` basis vector column `a, c`.
- The `v` component of the vector scales the `j` basis vector column `b, d`.

Then, the now scaled vectors `i` (`<ua, uc>`) and `j` (`<vb, vd>`) are added to produce the final vector sum: `<(ua + vb), (uc + vd)>`.

See [[Matrix Multiplication]]

See [[Linear Transformation Matrix Intuition]]
