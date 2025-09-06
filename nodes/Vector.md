---
context:
  - "[[Mathematics]]"
  - "[[Linear Algebra]]"
---

# Vector

Multidimensional quantity.

---

Ordered collection of multiple numbers used together as a single whole.

The fundamental object within a [[Vector Space]], governed by its axioms.

Vectors represent things that cannot be described by a single [[Scalar]] alone.

Representation of movement with direction and magnitude.

**Components**: A vector itself is defined by its components. The number of components matches the dimension of a vector. For example in 2D, the components are `<x, y>`; in 3D, they are `<x, y, z>`, and so on.

- Vectors that have the same components are the same vector.

**Context**: Depending on the context, vectors can represent different things. For example the vector `<5, 60>` can be used to represent:

- Ordered pair of the numbers `5` and `60`.
- Location in a [[Coordinate System]] where `x: 5` and `y: 60`.
- Force with a magnitude of `5`, directed at `60` degrees.

**Etymology**: A vector is what is needed to "carry" the point `A` to the point `B`. The Latin translation of 'vector' means 'carrier'.

**Geometric Representation**: Graphically represented by a directed line segment - an arrow.

## Vector Space

Vectors exist within a structured set of rules called a [[Vector Space]]. This is the formal mathematical 'universe' of vectors.

A vector space defines the rules that all vectors and their operations must follow.

See [[Vector Space]]

## Coordinate Systems

The primary way to represent, model, and work with vectors in a [[Vector Space]] is through a [[Coordinate System]], most commonly the [[Cartesian Coordinate System]].

_The vector space defines the rules, while the coordinate system provides the framework._

**Interpretation**: The coordinate system is useful to represent the geometry of vectors, while the vectors are useful to represent various quantities in the coordinate system.

**Context**: The meaning of a vector is dependent on context. For example, the `<x, y>` components of a vector can represent the `(x, y)` point location in space, or they could also represent a displacement in space by `(x, y)` units.

**Any Dimension**: Vectors work with coordinate systems of any Euclidean dimension.

## Magnitude

The magnitude of a vector is a scalar quantity representing its length, independent of direction.

**Hypotenuse**: In relation to axes in coordinate space, the vector line segment (from tail to head) can be seen as the hypotenuse of a right triangle. This hypotenuse is the magnitude (length) of the vector.

**Hypotenuse**: When a vector is positioned with its tail at the origin, the line segment from the origin to the vector's head forms the hypotenuse of a right triangle with legs along the coordinate axes. This hypotenuse is the magnitude (length) of the vector.

**Calculating Magnitude**: To calculate the magnitude, use the [[Pythagorean Theorem]]:

```
x² + y² = magnitude²

magnitude = √(x² + y²)
```

- For example, the vector `<4, 3>` has a magnitude of `5`.

**Always Positive**: The formula does not produce negative values. This is a good feature as a negative magnitude wouldn't make much sense.

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

## Interpolating Vectors

Vectors can be interpolated, finding any target point between them.

See [[Linear Interpolation]]

Given two vectors `A` and `B` (which can represent anything), linear interpolation finds a vector `C` that is a fraction of the way from `A` to `B`.
