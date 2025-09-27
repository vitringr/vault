---
aliases:
context:
---

#wip

# Quaternion

ad

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
