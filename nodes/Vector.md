---
context:
  - "[[Mathematics]]"
  - "[[Linear Algebra]]"
---

# Vector

Multidimensional quantity.

---

Entity with both magnitude and direction.

Ordered collection of numbers used together as a single entity.

**Components**: A vector itself is defined by its components. The number of components determines its dimension.

**Equality**: Two vectors are equal only if all corresponding components are identical.

**Etymology**: A vector is what is needed to "carry" the point `A` to the point `B`. The Latin translation of 'vector' means 'carrier'.

See [[Vector Operations]]

## Interpretation

**Abstraction**: Vectors are a versatile abstraction, capable of describing various types of information, with their meaning defined by context.

**Multidimensional**: Vectors represent multidimensional quantities that cannot be fully described by a single [[Scalar]] alone.

For example the vector `<5, 60>` can be used to represent:

- Ordered pair of the numbers `5` and `60`.
- Location in space where `x: 5` and `y: 60`.
- Force with a magnitude of `5`, directed at `60` degrees.

## Representation

Graphically represented as a directed line segment (an arrow) in space.

- _Tail_: Starting point of the vector.
- _Head_: Ending point of the vector.
- _Direction_: Orientation of the arrow.
- _Magnitude_: Length of the arrow.

## Magnitude

The magnitude of a vector is a scalar quantity representing its length, independent of direction.

**Hypotenuse**: When a vector is positioned with its tail at the origin, the line segment from the origin to the vector's head forms the hypotenuse of a right triangle with legs along the coordinate axes. This hypotenuse is the magnitude (length) of the vector.

**Calculating Magnitude**: To calculate the magnitude, use the [[Pythagorean Theorem]]:

```
x² + y² = magnitude²

magnitude = √(x² + y²)
```

- For example, the vector `<4, 3>` has a magnitude of `5`.

**Always Positive**: The formula does not produce negative values. This is a good feature as a negative magnitude wouldn't make much sense.

## Mathematical Foundation

_The vector space defines the rules, while the coordinate system provides the framework._

**Vector Space**: Vectors exist within the axiomatic framework of a [[Vector Space]], which defines the rules for vector operations and ensures consistency across different vector implementations.

**Coordinate Systems**: Vectors are typically represented and manipulated using a [[Coordinate System]], most commonly the [[Cartesian Coordinate System]], which provides a geometric interpretation of vector components.

**Basis Vectors**: Any vector can be represented by a linear combination of [[Basis Vectors]] that define the coordinate system's axes.
