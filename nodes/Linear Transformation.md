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

Formally, it is a [[Function (Mathematics)|Function]] that preserves [[Vector]] addition (`F(a + b) = F(a) + F(b)`) and [[Scalar]] multiplication (`F(ka) = kF(a)`).

**Function**: Takes a [[Vector]] as input, and returns a vector as output, while respecting the underlying core structure of the vector space.

**Geometric Interpretation**: In [[Geometry]], linear transformations often correspond to operations such as _rotation_, _scaling_, _reflection_, _shearing_, _projection_, or any combination between them.

Linear transformations do not contain translation. #wip

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

## Determinant

The determinant describes how a linear transformation affects the scaling of space.

See [[Determinant]]

## Common Transformations

#wip

**Rotation**: Rotating space by an angle around a point in 2D or axis in 3D.

**Scale**: Scaling space by a scalar factor.

- _Uniform scale_ is when the entire space is scaled uniformly, thus preserving angles and proportions.
- _Nonuniform scale_ is when different scale factors are applied to different axes, resulting in "squashed" or "stretched" space.

**Projection**: Refers to any dimension-reducing operation.

**Prespective Projection**: #wip

**Parallel Projection**: One way to achieve this is to use a scale factor of zero in a direction. In this case, all points are flattened/projected onto a perpendicular axis (in 2D) or plane (in 3D).

- It is called "parallel" because the lines from the original points to their projected counterparts are parallel.
- Projection onto a cardinal axis occurs by simply discarding one of the dimensions, or scaling it by zero.

**Reflection**: Transformation that mirrors space about a line (in 2D) or plane (in 3D). Reflection is accomplished by applying a scale factor of `-1`.

**Shear**: Shearing is a transformation that "skews" space, stretching it non-uniformly. Angles are not preserved, but areas and volumes are.

- The basic idea is to add a multiple of one coordinate to the other.
