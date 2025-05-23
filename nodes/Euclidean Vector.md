---
aliases:
  - Geometric Vector
  - Spatial Vector
context:
  - "[[Vector]]"
  - "[[Geometry]]"
---

#wip

# Euclidean Vector

Geometric object that has magnitude and direction.

---

Frequently represented by a directed line segment.

**Magnitude**: the length or size of the vector.
**Direction**: indicates where the vector is pointing.

The direction can also be represented by an angle.

**Components**: A vector has a horizontal part and a vertical part, called components. Vectors that have the same components are the same vector.

Vectors are a way of describing movement with math.

**Etymology**: A vector is what is needed to "carry" the point `A` to the point `B`. The Latin translation of 'vector' means 'carrier'.

## Coordinates

Vectors can represent points in a [[Cartesian Coordinate System]].

The `<x, y>` components of a vector represent the `(x, y)` point in space.

**Any Dimension**: This works for coordinate systems of any Euclidean dimension. For example in 3D, the vector `<x, y, z>` represents the point `(x, y, z)`.

**Arrow**: Visualizing the vector as an arrow with a direction and magnitude, the `(x, y)` points in space are arrows that start with tails from the origin `(0, 0)` and end with heads at the `(x, y)` point itself.

## Magnitude

The magnitude of a vector is its length.

The components of a vector (`x` and `y`) form a right triangle. Imagine vectors `(x, 0)` and `(0, y)` as the triangle sides, and `(x, y)` as the hypotenuse.

Since the length of the vector `(x, y)` is the length of the hypotenuse, it can be found by using the [[Pythagorean Theorem]]:

```
x² + y² = magnitude²

magnitude = sqrt(x² + y²)
```

One nice thing about this formula is that it cannot produce negative values, and a negative magnitude wouldn't really make sense.

## Vector Algebra

Vectors can be operated with algebraically.

**Combination**: Multiple vectors can be combined into one by adding their components together.

```
<ax, ay> + <bx, by> = <ax + bx, ay + by>

<ax, ay> - <bx, by> = <ax - bx, ay - by>
```

Multiple 'steps' from an origin to a destination can be expressed by a single step of their sum directly.

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

```language
vA + ? = vC

? = vC - vA
```

Visually, this works by placing the tails (begin points) two different vectors on the same point, and finding the path between their heads (arrows).

The distance between those two vectors is the magnitude of the path.

## Average

The vector whose head is halfway between the heads of `<x, y>` and `<a, b>` is the average of each pair of components, or `<(x + a) / 2, (y + b) / 2>`.

By this logic, vectors can be [[Linear Interpolation|linearly interpolated]] to find any point on the line between them.
