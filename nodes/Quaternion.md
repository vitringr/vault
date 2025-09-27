---
context:
  - "[[Mathematics]]"
---

#wip

# Quaternion

ad

---

Contains a scalar component `w` and a vector component `v`. They are related to the angle of rotation `θ` and the axis of rotation `n` by: `w = cos(θ/2)` and `v = n sin(θ/2)`.

---

Quaternion multiplication can be used to concatenate multiple rotations.

---

Uses four numbers to express orientation.

Detaile understanding of quaternions is not needed to use them, but one needs to understand what quaternions can do.

Contains a scalar component and a vector component. Closely related to the [[Axis-Angle Representation]] form.

## Negation

Quaternions can be negated by negating each component:

`- [w (x y z)] = [-w (-x -y -z)]`

Negating a quaternion doesn't really do anything, at least in the context of angular displacement.

> The quaternions `q` and `-q` describe the same angular displacement. Any angular displacement in 3D has exactly two representations in quaternion format, and they are negatives of each other.

## Identity

Geometrically, there are two identity quaternions:

`[1 0]` and `[-1 0]`

They represent no angular displacement.

Algebraically, only the `[1 0]` is an identity quaternion.

## Magnitude

[[Pythagorean Theorem]]

The magnitude of `[w (x y z)]` is `√(w² + x² + y² + z²)`.

All quaternions that represent angular displacements are unit quaternions with magnutude equal to `1`.

## Conjugate

The _conjugate_ of a quaternion, denoted `q*`, is obtained by negating the vector portion of the quaternion.

`q* = [w v]* = [w -v] = [w (x y z)]* = [w (-x -y -z)]`

## Inverse

The inverse of a quaternion, denoted `q⁻¹` is defined as the conjugate of a quaternion divided by its magnitude.

`q⁻¹ = q* / ||q||`

The quaternion inverse has an interesting correspondence with the [[Multiplicative Inverse]] for real numbers.

When we multiply a quaternion `q` by its inverse `q⁻¹`, we get the identity quaternion `[1 0]`.

## Multiplication

Quaternion multiplication is associative: `(ab)c = a(bc)`
Quaternion multiplication is not commutative: `ab ≠ ba`

The magnitude of a quaternion product is equal to the product of the magnitudes: `||q₁ * q₂|| = ||q₁|| * ||q₂||`

This is significant as it guarantees that multiplying two unit quaternions results in a unit quaternion.

The inverse of a quaternion product is equal to the product of the inverses in a reversed order: `(a * b)⁻¹ = b⁻¹ * a⁻¹`

## Exponentiation

Raising a quaternion to a scalar power.

If `q` represents a clockwise rotation of `30º` about the `x`-axis, then `q²` represents a clockwise rotation of `60º` about the `x`-axis, and `q` to the power of `-1/3` represents a counterclockwise rotation of `10º` about the `x`-axis.

The inverse `q⁻¹` can also be interpreted in this context and the result is as expected - the quaternion that performs the opposite rotation.

### Rotation Loss

> [!WARNING] Rotation Loss
> Multiple spins cannot be represented.

**Shortest Arc**: Quaternions represent angular displacements using the shortest arc. Multiple spins cannot be represented. For example, if `q` is `30º` clockwise, `q⁸` is not a `240º` clockwise rotation; it is `120º` counterclockwise rotation. Quaternions only capture the end result.

In situations that care about the total amount of rotation quaternions are not the right tool for the job.

### Zero to One

For any scalar `a` besides zero, `a⁰ = 1` and `a¹ = a`. As the exponent `ⁿ` varies from `0` to `1`, the value of `aⁿ` varies from `1` to `a`. Quaternion exponentiation is similar. As `ⁿ` varies from `0` to `1`, the quaternion exponentiation `qⁿ` varies from `[1 0]` to `q`.

This is useful as it allows calculating a fraction of an angular displacement.

For example, to compute a quaternion that represents one third of the angular displacement of `q`, compute `q` to the power of `1/3`.

## Slerp
