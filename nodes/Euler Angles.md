---
context:
  - "[[Geometry]]"
  - "[[Rotation]]"
---

#wip

# Euler Angles

ad

---

Euler angles store orientation by using three numbers. These numbers represent ordered rotation angles about the three object-space axes.

**Intuitive**: Euler angles are more intuitive for humans to work with compared to other methods of representing orientation, such as [[Quaternion]].

**Memory-Efficient**: Euler angles use the minimum amount of data possible for storing an orientation in 3D.

**Always Valid**: There is no such thing as an invalid set of Euler angles. Any three numbers have a meaningful interpretation.

**Gimbal Lock**: Euler angles suffer from [[Gimbal Lock]].

**Aliasing**: Euler angles suffer from aliasing problems due to the cyclic nature of rotation angles and because the rotations are not completely independent of one another. There are solutions and workarounds to simple forms of aliasing.

**Problematic Interpolation**: [[Interpolation]] between Euler angle orientations can cause errors and undesired results.
