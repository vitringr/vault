---
context:
  - "[[Gradient Noise]]"
---

# Perlin Noise

Classic [[Gradient Noise]] generation algorithm.

---

Generates smooth, natural-looking patterns.

## Algorithm

1. First, construct a [[Lattice]] of squares.
2. Assign a random unit gradient [[Vector]] to each lattice vertex.

For each query point inside a lattice cell:

3. Determine the four surrounding vertices and compute the displacement vectors from the point to each vertex.
4. Calculate the dot products between these displacement vectors and their corresponding vertex's gradient vectors.
5. [[Interpolation|Interpolate]] the resulting dot products via smooth [[Easing Function|easing]] of [[Bilinear Interpolation]] to get the final value of the point.

> [!NOTE] Terminology
>
> - _gradient vector_: the predefined random unit vector.
> - _displacement vector_: vector difference from point to gradients.

See [[Perlin Noise Implementation]]
