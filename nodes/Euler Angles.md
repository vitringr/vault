---
context:
  - "[[Rotation]]"
  - "[[Rotation Representation]]"
---

# Euler Angles

System to represent 3D orientation as three sequential rotations around fixed axes.

---

Euler angles define orientation using three numbers, each representing an ordered rotation angle about specific axes.

## Properties

Advantages:

**Intuitive**: Euler angles are more intuitive for humans to work with compared to other methods of representing orientation, such as [[Quaternion]].

**Memory-Efficient**: Euler angles use the minimum amount of data possible for storing an orientation in 3D.

**Always Valid**: There is no such thing as an invalid set of Euler angles. Any three numbers have a meaningful interpretation.

Disadvantages:

**Gimbal Lock**: Euler angles suffer from [[Gimbal Lock]].

**Aliasing**: Multiple angle combinations can represent the same orientation due to the cyclic nature of angles. There are workarounds for some simple forms of aliasing.

**Unstable Interpolation**: Direct [[Interpolation]] between Euler angles is problematic, causing errors and producing unnatural motion.
