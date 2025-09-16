---
context:
  - "[[Linear Transformation]]"
---

#wip

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

Can be though of as a special case of scaling with a factor of `-1` along one axis.

- Preserves lengths and angles, but reverses orientation.
- Determinant equals `-1`.
- Invertible.

## Shear

Shearing is a transformation that "skews" space, stretching it non-uniformly. Angles are not preserved, but areas and volumes are.

- The basic idea is to add a multiple of one coordinate to the other.

## Projection

Refers to any dimension-reducing operation.

**Non-Invertible**: This is the only non-invertible primitive linear transformation.

## Prespective Projection

## Parallel Projection

One way to achieve this is to use a scale factor of zero in a direction. In this case, all points are flattened/projected onto a perpendicular axis (in 2D) or plane (in 3D).

- It is called "parallel" because the lines from the original points to their projected counterparts are parallel.
- Projection onto a cardinal axis occurs by simply discarding one of the dimensions, or scaling it by zero.

