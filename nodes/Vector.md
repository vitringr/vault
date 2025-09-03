---
context:
  - "[[Mathematics]]"
---

# Vector

Multidimensional quantity.

---

Collection of multiple numbers used together as a single whole.

Vectors are useful to describe things that cannot be represented by a single [[Scalar]] such as coordinates in ≥2D space, movement, various forces, and so on.

**Components**: Vectors have a component 'part' for each dimension. For example in 2D, the components are `<x, y>`; for 3D, they are `<x, y, z>`, and so on. Vectors that have the same components are the same vector.

**Context**: Depending on the context, vectors can represent different things. For example the vector `<5, 60>` can be used to represent:

- Ordered pair of the numbers `5` and `60`.
- Location in a [[Coordinate System]] where `x: 5` and `y: 60`.
- Force with a magnitude of `5`, directed at `60` degrees.

**Etymology**: A vector is what is needed to "carry" the point `A` to the point `B`. The Latin translation of 'vector' means 'carrier'.

**Visual Representation**: Represented by a directed line segment.

## Coordinate Systems

Vectors are a fundamental concept used to represent various quantities in a [[Coordinate System]], such as coordinates or displacements.

See [[Cartesian Coordinate System]]
See [[Polar Coordinate System]]

**Meaning**: The meaning of a vector is dependent on context. For example, the `<x, y>` components of a vector can represent the `(x, y)` location in space, or a displacement in space by `(x, y)` units.

**Any Dimension**: This works for coordinate systems of any Euclidean dimension. For example in 3D, the vector `<x, y, z>` represents the point `(x, y, z)`.

**Visualization**: Visualizing the vector as an arrow with a direction and magnitude, the `(x, y)` points in space are arrows that start with tails from the origin `(0, 0)` and end with heads at the `(x, y)` point itself.

## Magnitude

The magnitude of a vector is a scalar quantity representing its length, independent of direction.

**Hypotenuse**: When positioned in relation to axes in coordinate space, the components of a vector can form a right triangle. The hypotenuse of that triangle (from some origin `<ox, oy>` to the vector `<x, y>`) is the magnitude (length) of the vector.

**Calculating Magnitude**: To find the magnitude, use the [[Pythagorean Theorem]]:

```
x² + y² = magnitude²

magnitude = √(x² + y²)
```

For example, the vector `<4, 3>` has a magnitude of `5`.

**Always Positive**: A feature of this formula is that it doesn't produce negative values. This is good because a negative magnitude wouldn't really make much sense.

---

#wip

## Negation

Vectors can be negated, meaning that every component is negated.

`-<x, y> = <-x, -y>`

For example, negating `<5, -3>` results in `<-5, 3>`.

**Result**: Negating a vector `v` results in its _additive inverse_ `-v` such that `v + (-v) = 0`.

**Reverse Direction**: Nagating a vector results in a vector of the same magnitude but opposite direction.

- Visually, it's the same line segment, but with the arrowhead on the other side.

## Scaling

Vectors can be multiplied by scalars, meaning that every component is multiplied by the scalar.

`s * <x, y> = <sx, sy>`

For example, multiplying the vector `<5, -3>` by the scalar `2` results in `<10, -6>`.

**Result**: The result is a vector parallel to the original vector, with a different length and possibly opposite direction.

**Division**: Same idea due to [[Reciprocal Multiplication]].

**Negation**: Vector negation can be viewed as the specific case of multiplying a vector by the scalar `-1`.

**Geometric Intuition**: Multiplying a vector by a scalar `s` has the effect of scaling the length by a factor of `|k|`. If `k < 0`, then the direction is also flipped.

## Addition and Subtraction

Vectors can be added and subtracted, meaning that every component from vector `B` gets added/subtracted to/from vector `A`.

```
<ax, ay> + <bx, by> = <(ax + bx), (ay + by)>
<ax, ay> - <bx, by> = <(ax - bx), (ay - by)>
```

For example, the sum of vectors `<5, -3>` and `<-1, 2>` equals `<4, -1>`.

**Additive Inverse**: Subtracting vector `B` from vector `A` can also be viewed as adding vector `B` additive inverse `-B` to vector `A`.

**Result**: The result of adding/subtracting `B` to/from `A` is a new vector `C` which starts from vector `A` as origin and ends at the resulting coordinate.

#wip

---

## Vector Algebra

Vectors can be operated with algebraically.

**Combination**: Multiple vectors can be combined into one by adding their components together.

```
<ax, ay> + <bx, by> = <ax + bx, ay + by>

<ax, ay> - <bx, by> = <ax - bx, ay - by>
```

Movement destination can be expressed by the sum of the origin and the displacement.

## Scaling

To scale a vector, multiply both of its components by a [[Scalar]].

```
w = <x, y>
wk = <kx, ky>
```

Scaling a vector by positive scalars results in a vector pointed at the same direction, but with a different length.

Scaling a vector by a negative scalars reverses its direction.

```
<x, y> * -1 = <-x, -y>

<3, -12.4> * 3 = <9, -37.2>
```

Multiplying a vector by a scalar can scale it up when the scalar magnitude is bigger than `1`, or scale it down when it is between `0` and `1`.

## Path

The path from vector `A` to vector `B` is vector `C`:

```
vA + vB = vC
```

To find the unknown path from a known starting point `A` to a known end point `C`, find the difference between them:

```
vA + ? = vC

? = vC - vA
```

Visually, this works by placing the tails (begin points) two different vectors on the same point, and finding the path between their heads (arrows).

The distance between those two vectors is the magnitude of the path.

## Average

The vector whose head is halfway between the heads of `<x, y>` and `<a, b>` is the average of each pair of components, or `<(x + a) / 2, (y + b) / 2>`.

By this logic, vectors can be [[Linear Interpolation|linearly interpolated]] to find any point on the line between them.
