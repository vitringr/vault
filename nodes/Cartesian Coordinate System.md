---
context:
  - "[[Coordinate System]]"
---

# Cartesian Coordinate System

Coordinate system that specifies each point uniquely in a plane by a set of numerical coordinates.

---

**Coordinates**: The coordinates are the components of a [[Vector]] from the origin to the point.

**Axes**: The coordinate lines. The axes are generally _x_ (horizontal) and _y_ (vertical).

- A single axis is essentially a [[Number Line]]. It extends infinitely in either direction.
- The system can be extended to multiple dimensions. For 3D coordinates, a _z_ axis is added as depth.
- The axes are generally perpendicular to each other, although this is arbitrary.

**Origin**: The point where all the axes intersect. Has `[0, 0]` as coordinates.

## Conventions

Different systems might use different conventions regarding the axes directions.

**2D**: The standard mathematical convention for 2D is that `+x` points right (East), and `+y` points up (North). However, it is common for systems to reverse the `y` axis direction, especially when dealing with screens that are to be viewed from top to an infinite bottom.

**3D**: For 3D space, one standard convention is the 'left hand' one, where `+x`, `+y`, and `+z` point right, up, and forward, respectively.

These different coordinate systems can be transformed from one to the other.

## Vector Space

The Cartesian coordinate system provides the perfect framework for [[Vector]] representation.

Vectors are perfect for describing displacement, which means they can also describe positions in space, since any position can be described by a displacement from the origin.
