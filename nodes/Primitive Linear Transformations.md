---
context:
  - "[[Linear Transformation]]"
---

# Primitive Linear Transformations

The fundamental [[Linear Transformation]] types. More complex linear transformations can be decomposed into a combination of these basic operations.

---

## Rotation

Rotates space around the origin (in 2D), or around an axis through the origin (in 3D) by a given angle.

- Preserves lengths, angles, and orientation.
- Determinant equals `1`.
- Invertible.

## Scaling (Dilation)

Transformation that scales space along specific axes by [[Scalar]] factors.

- Preserves the origin.
- Determinant equals the product of the scale factors.
- Invertible as long a no scale factor is zero.

_**Uniform Scale**_: The entire space is scaled uniformly, thus preserving angles and proportions.

_**Non-uniform scale**_: Scale factors differ between axes. Does not preserve angles, but parallel lines remain parallel. Results in "squashed" or "stretched" space.

## Reflection

Transformation that mirrors space across a line (in 2D) or plane (in 3D) that passes through the origin.

Can be though of as a special case of scaling by a factor of `-1` along one axis.

- Reverses orientation.
- Preserves lengths and angles.
- Determinant equals `-1`.
- Invertible.

## Shear

Transformation that "skews" space, adding a multiple of one coordinate to another.

Moves points in a direction parallel to an axis by an amount proportional to their coordinate on another axis.

Example: `x' = x + ay`, `y' = y`.

- Does not preserve angles.
- Preserves area (in 2D) and volume (in 3D).
- Determinant equals `1`.
- Invertible.

## Projection

Dimension-reducing transformation.

Flattens space onto a subspace (like a line or plane) that passes through the origin.

This is the only non-invertible primitive linear transformation. Once projected, a dimension of information is lost.

- Determinant equals `0`.
- Non-invertible.
