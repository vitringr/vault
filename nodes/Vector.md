---
context:
  - "[[Mathematics]]"
---

# Vector

Multidimensional quantity.

---

Vectors are useful to describe things that cannot be represented by a single [[Scalar]] such as coordinates in ≥2D space, movement, various forces, and so on.

**Components**: Vectors have a component 'part' for each dimension. For example in 2D, the components are `<x, y>`; for 3D, they are `<x, y, z>`, and so on. Vectors that have the same components are the same vector.

**Context**: Depending on the context, vectors can represent different things. For example the vector `<5, 60>` can be used to represent:

- Ordered pair of the numbers `5` and `60`.
- Location in a [[Coordinate System]] where `x: 5` and `y: 60`.
- Force with a magnitude of `5`, directed at `60` degrees.

**Etymology**: A vector is what is needed to "carry" the point `A` to the point `B`. The Latin translation of 'vector' means 'carrier'.

**Visual Representation**: Represented by a directed line segment.

## Coordinate System

Vectors can represent coordinates in a [[Coordinate System]].

### Cartesian Coordinates

See [[Cartesian Coordinate System]]

The `<x, y>` components of a vector represent the `(x, y)` point in space.

**Any Dimension**: This works for coordinate systems of any Euclidean dimension. For example in 3D, the vector `<x, y, z>` represents the point `(x, y, z)`.

**Visualization**: Visualizing the vector as an arrow with a direction and magnitude, the `(x, y)` points in space are arrows that start with tails from the origin `(0, 0)` and end with heads at the `(x, y)` point itself.

### Polar Coordinates

See [[Polar Coordinate System]]

**Visualization**: The vector can represent an arrow with both magnitude and direction.

## Magnitude

The magnitude of a vector is its length.

### Calculating Magnitude

When positioned in relation to axes in coordinate space, the components of a vector can form a right triangle. The hypotenuse of that triangle (from some origin `<ox, oy>` to the vector `<x, y>`) is the magnitude (length) of the vector.

To find the magnitude, use the [[Pythagorean Theorem]]:

```
x² + y² = magnitude²

magnitude = √(x² + y²)
```

**Always Positive**: A feature of this formula is that it doesn't produce negative values. This is good because a negative magnitude wouldn't really make much sense.

## Vector Algebra

Vectors can be operated with algebraically.

**Combination**: Multiple vectors can be combined into one by adding their components together.

```
<ax, ay> + <bx, by> = <ax + bx, ay + by>

<ax, ay> - <bx, by> = <ax - bx, ay - by>
```

Movement destination can be expressed by the sum of the origin and the movement.

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
