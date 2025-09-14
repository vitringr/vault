---
context:
  - "[[Vector]]"
---

#wip

# Vector Operations

ad #wip

---

## Context

## Coordinate Systems

The primary way to represent, model, and work with vectors in a [[Vector Space]] is through a [[Coordinate System]], most commonly the [[Cartesian Coordinate System]].

**Interpretation**: The coordinate system is useful to represent the geometry of vectors, while the vectors are useful to represent various quantities in the coordinate system.

**Context**: The meaning of a vector is dependent on context. For example, the `<x, y>` components of a vector can represent the `(x, y)` point location in space, or they could also represent a displacement in space by `(x, y)` units.

**Any Dimension**: Vectors work with coordinate systems of any Euclidean dimension.


## Negation

Vectors can be negated by negating all of their components:

`-<x, y> = <-x, -y>`

For example, negating the vector `<5, -3>` results in `<-5, 3>`.

**Additive Inverse**: Negating a vector `v` results in its _additive inverse_ `-v` such that `v + (-v) = 0`.

**Reverse Direction**: Nagating a vector results in a vector of the same magnitude but opposite direction.

- Visually, it's the same line segment, but with the arrowhead on the other side.

## Scaling

Vectors can be scaled by multiplying all of their components by a [[Scalar]] value:

`s * <x, y> = <sx, sy>`

For example, multiplying the vector `<5, -3>` by the scalar `2` results in `<10, -6>`.

**Result**: The result is a vector parallel to the original vector, with a different length and possibly opposite direction.

**Division**: Any division can replaced by a [[Reciprocal Multiplication]] operation.

**Negation**: Vector negation can be viewed as the specific case of multiplying a vector by the `-1` scalar.

**Geometric Intuition**: Multiplying a vector by a scalar `s` has the effect of scaling the length by a factor of `|s|`. If `s < 0`, then the direction is also flipped.

## Addition and Subtraction

Vectors can be added/subtracted together by adding/subtracting every component from vector `A` to/from the same component in vector `B`.

```
<ax, ay> + <bx, by> = <(ax + bx), (ay + by)>
<ax, ay> - <bx, by> = <(ax - bx), (ay - by)>
```

For example, the sum of vectors `<5, -3>` and `<-1, 2>` equals `<4, -1>`.

**Additive Inverse**: Subtracting vector `B` from vector `A` can be viewed as adding vector `B`'s additive inverse `-B` to vector `A`.

**Result**: The result of adding/subtracting vectors `A` and `B` is vector `C`, which equals their combined total displacement.

See [[Vector Displacement Intuition]].

## Unit Vector

Unit vector is a vector with a magnitude of `1`.

Unit vectors are concerned with direction only, not magnitude.

**Trigonometry**: This is a fundamental concept in [[Trigonometry]], which uses the unit vector and unit circle concepts heavily.

## Normalization

Any nonzero vector can be _normalized_, producing a unit vector that points in the same direction.

To normalize a vector, divide each of its components by its magnitude.

See [[Vector Normalization]]

## Distance Formula

The distance between two points is equal to the length of an imaginary line that connects them.

To calculate the distance between vectors `A` and `B`, calculate the magnitude of their difference vector `D = A - B`.

See [[Distance Formula]]

## Dot Product

The dot product is the sum of the products of corresponding vector components.

```
A·B = A.x * B.x + A.y * B.y + ... + A.n * B.n
```

See [[Dot Product]]

## Interpolating Vectors

Vectors can be interpolated, finding any target point between them.

Given two vectors `A` and `B`, linear interpolation finds a vector `C` that is a fraction of the way from `A` to `B`.

See [[Linear Interpolation]]
