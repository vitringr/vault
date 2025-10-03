---
context:
  - "[[Rotation]]"
---

# Rotation Representation

Common ways of representing [[Rotation]] mathematically.

---

See [Rotation in Three Dimensions](https://gamemath.com/book/orient.html)

## Rotation Matrix

See [[Rotation Matrix]]

Represents rotation by standard matrix transformation.

**Pros**: Simple composition, direct application to [[Vector|Vectors]].
**Cons**: Over-parametarized, numerical drift, inefficient for [[Interpolation]].

## Euler Angles

See [[Euler Angles]]

Represents rotation as three sequential rotations around the primary axes.

**Pros**: Intuitive and memory-efficient.
**Cons**: [[Gimbal Lock]], multiple aliases, complex composition, unstable interpolation.

## Axis-Angle Representation

See [[Axis-Angle Representation]]

Unit vector that describes the axis of rotation and a scalar for the angle magnitude.

**Pros**: Intuitive, minimal representation, no gimbal lock.
**Cons**: Singularity at `180°`, messy composition, poor for interpolation.

## Quaternion

See [[Quaternion]]

Four-dimensional number system that compactly and robustly represents three-dimensional rotations.

**Pros**: Smooth interpolation, efficient composition, numerically stable, no gimbal lock.
**Cons**: Unintuitive, requires normalization.
