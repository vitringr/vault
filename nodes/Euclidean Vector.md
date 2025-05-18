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

## Vector Algebra

Vectors can be operated with algebraically.

**Combination**: Multiple vectors can be combined into one by adding their components together.

```
<ax, ay> + <bx, by> = <ax + bx, ay + by>

<ax, ay> - <bx, by> = <ax - bx, ay - by>
```

Multiple 'steps' from an origin to a destination can be expressed by a single step of their sum directly.

**Scaling**: Vectors can be scaled by [[Scalar]] numbers.

```
<x, y> * -1 = <-x, -y>

<3, -12.4> * -3 = <-9, 37.2>
```

Multiplying a vector by a negative number reverses its direction.

Multiplying a vector by a scalar can scale it up when the scalar magnitude is bigger than `1`, or scale it down when it is between `0` and `1`.
