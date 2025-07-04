---
context:
  - "[[Computer Graphics]]"
---

# Geometry Instancing

The practice of rendering multiple copies of the same mesh in a scene at once.

---

Optimization technique.

## Intuition

Drawing `100` point particles on the screen requires the data of `100` vertices.

Drawing `100` of the same triangle particles on the screen would require `300` vertices - `100` for each triangle vertex A, and `100` and `100` for the other two vertices B and C.

This redundant data is inefficient.

Instead, store the geometry once (just `3` vertices for the triangle), and then store instance data separately - `100` particle positions.
