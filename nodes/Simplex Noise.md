---
context:
  - "[[Gradient Noise]]"
---

#wip

# Simplex Noise

Advanced [[Gradient Noise]] algorithm.

---

Generates smooth, natural-looking patterns.

Can efficiently scale up to higher dimensions.

**Simplex Space**: Uses the concept of [[Simplex]] space, constructing a lattice of simplex shapes, depending on the dimension.

**Efficiency**: Each point gets contribution from its surrounding vertices in simplex space. This can be more efficient than [[Perlin Noise]], as the vertices needed for calculation are reduced.

## Algorithm

Note that this is the 2D variant of simplex noise. It could also scale up for higher dimensions.

### Gradients

#wip

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
