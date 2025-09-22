---
context:
  - "[[Noise (Procedural Generation)]]"
---

# Value Noise

Basic [[Noise (Procedural Generation)|Noise]] generation algorithm.

---

Probably the simplest and fastest noise generation method.

**Blocky**: Can appear "blocky" due to direct [[Scalar|scalar]] value interpolation.

## Implementation

**Grid**: Define a [[Lattice]] of points and assign a random value to each point.

**Interpolation**: For any given point between grid cells, compute a value by [[Interpolation|interpolating]] with the surrounding lattice points.

**Output**: The final interpolated values produce a continuous pattern.

See [[Value Noise Implementation]]
