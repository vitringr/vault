---
context:
  - "[[Gradient Noise]]"
---

#wip

# Simplex Noise

Advanced [[Gradient Noise]] generation algorithm.

---

Generates smooth, natural-looking patterns.

Works by calculating contribution for each point from nearby direction [[Vector|Vectors]] in [[Simplex]] space. Transforms the [[Lattice]] from simplex space to normal square space, and vice versa. Square space helps with calculations, while simplex space is where the algorithm does the core work.

**Dimensions**: Can efficiently scale up to higher dimensions. Every dimension has its own simplex shape that the algorithm can use.

**Efficiency**: Since the lattice is in simplex space, each point gets contributions from the minimum amount of surrounding vertices possible, based on the dimension. This is an improvement over [[Perlin Noise]], as the vertices needed for calculation are reduced.

## Algorithm

Note that this is the 2D variant of simplex noise. The same logic applies for higher dimensions.

### Gradients

Create an array of gradient vectors with different directions.

Imagine those direction vectors as being "attached" on every square lattice cell vertex.

These direction vectors are used to determine the noise value for points inside the cell, considering their direction, and the distance between each point and a given vector.

Normally, every point would be inside a square cell that has 4 vertices. But the trick here is that after transforming the space into simplex space, every point is then inside a triangular cell, having only 3 vertices. That means that every point will be affected by 3 surrounding gradient vectors in simplex space.

### Permutation Table

#wip

Create a permutation table of pseudorandom numbers used to choose a gradient based on input.

Having a consistent way of choosing gradients ensures that similiar numbers will choose similiar gradients, producing the continuous output effect.

> [!TIP]
> Tested that having the permutation table from 0-255 in order just gives symmetry.

### Input

The algorithm expects input numbers in the form `(x, y)`.

```typescript
function noise(input_triangle_x: number, input_triangle_y: number) { ... }
```

Imagine the input coordinates as being in the simplex (equilateral triangle) space.

**Continuity**: If the numbers are continuous through different iterations, the algorithm should produce continuous results.

**Input Scale**: The input numbers `(x, y)` can be scaled, essentially 'zooming' in or out of the noise field.

### Transformation

#wip
