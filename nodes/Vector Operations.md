---
context:
  - "[[Vector]]"
---

# Vector Operations

List of fundamental [[Vector]] operations.

---

## Negation

Vectors can be negated by negating all of their components.

```
-<x, y> = <-x, -y>
```

For example, negating the vector `<5, -3>` results in `<-5, 3>`.

**Additive Inverse**: Negating a vector `v` results in its _additive inverse_ `-v` such that `v + (-v) = 0`.

**Reverse Direction**: Nagating a vector results in a vector of the same magnitude but opposite direction.

Visually, it's the same line segment, but with the arrowhead on the other side.

## Scaling

Vectors can be scaled by multiplying all of their components by a [[Scalar]] value:

```
s * <x, y> = <sx, sy>
```

For example, multiplying the vector `<5, -3>` by the scalar `2` results in `<10, -6>`.

**Result**: The result is a vector parallel to the original vector, with a different length and possibly opposite direction.

**Division**: Any division can replaced by a [[Reciprocal Multiplication]] operation.

**Negation**: Vector negation can be viewed as the specific case of multiplying a vector by the `-1` scalar.

**Geometric Intuition**: Multiplying a vector by a scalar `s` has the effect of scaling the length by a factor of `|s|`. If `s < 0`, then the direction is also flipped.

## Addition and Subtraction

Vectors can be added/subtracted together by adding/subtracting every component from vector `A` to/from the same component in vector `B`.

```
<ax, ay> + <bx, by> = <(ax + bx), (ay + by)>
```

```
<ax, ay> - <bx, by> = <(ax - bx), (ay - by)>
```

For example, the sum of vectors `<5, -3>` and `<-1, 2>` equals `<4, -1>`.

**Additive Inverse**: Subtracting vector `B` from vector `A` can be viewed as adding vector `B`'s additive inverse `-B` to vector `A`.

**Result**: The result of adding/subtracting vectors `A` and `B` is vector `C`, which equals their combined total displacement.

See [[Vector Displacement Intuition]].

## Normalization

Any nonzero vector can be _normalized_, producing a [[Unit Vector]] that points in the same direction.

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
