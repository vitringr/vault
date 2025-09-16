---
context:
  - "[[Linear Transformation]]"
---

#wip

# Primitive Linear Transformations

ad

---

#wip

## Rotation

Rotating space by an angle around a point in 2D or axis in 3D.

## Scale

Scaling space by a scalar factor.

- _Uniform scale_ is when the entire space is scaled uniformly, thus preserving angles and proportions.
- _Nonuniform scale_ is when different scale factors are applied to different axes, resulting in "squashed" or "stretched" space.

## Projection

Refers to any dimension-reducing operation.

**Non-Invertible**: This is the only non-invertible primitive linear transformation.

## Prespective Projection

## Parallel Projection

One way to achieve this is to use a scale factor of zero in a direction. In this case, all points are flattened/projected onto a perpendicular axis (in 2D) or plane (in 3D).

- It is called "parallel" because the lines from the original points to their projected counterparts are parallel.
- Projection onto a cardinal axis occurs by simply discarding one of the dimensions, or scaling it by zero.

## Reflection

Transformation that mirrors space about a line (in 2D) or plane (in 3D). Reflection is accomplished by applying a scale factor of `-1`.

## Shear

Shearing is a transformation that "skews" space, stretching it non-uniformly. Angles are not preserved, but areas and volumes are.

- The basic idea is to add a multiple of one coordinate to the other.
