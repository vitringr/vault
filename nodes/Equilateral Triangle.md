---
aliases:
  - Regular Triangle
context:
  - "[[Geometry]]"
---

# Equilateral Triangle

(aka. Regular Triangle)

Triangle in which all three sides have the same length, and all three angles are equal.

---

**Angles**: Three equal `60` degree angles.

**Height**: The height of an equilateral triangle equal to either:

- `base * sin(60)`
- `base * (sqrt(3) / 2)`
- `base * 0.8660254037844386`

## Centroid

The centroid can be constructed by finding the average coordinate of the vertices:

```
centroid.x = (a.x + b.x + c.x) / 3
centroid.y = (a.y + b.y + c.y) / 3
```

**Edge Distance**: The distance from the centroid to the closest edge point is equal to either:

- `base * (height / 3)`
- `base * (sqrt(3) / 6)`
- `base * 0.2886751345948129`

**Vertex Distance**: The distance from the centroid to a vertex is equal to the _circumradius_ of the triangle. It is also equal to _twice_ the distance from the closest edge.

- `base * (sqrt(3) / 3)`
- `base * 0.5773502691896257`

**Height Ratios**: Dividing the height into `3`, the first `1/3` is the distance from centroid to edge, then `2/3` is the distance from centroid to vertex, and `3/3` is the height itself.
