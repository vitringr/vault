---
context:
  - "[[Computer Graphics]]"
---

# Coordinate Systems in Computer Graphics

Common and useful [[Coordinate System]] variations used in [[Computer Graphics]].

---

It is very useful to have different coordinate systems for different situations, with the ability to transform between one another.

**World Space**: The global reference frame for all other coordinate systems.

**Local Space**: Coordinate system associated with a particular entity. The origin is at its pivot point, and its geometry is defined locally in this space.

**Upright Space**: Halfway between world space and local space. The axes of upright space are parallel with those of world space, but the origin of upright space matches the origin of local space.

**Camera Space**: Coordinate system from the camera's perspective. The camera itself is at the origin `(0,0,0)`, and its line of sight is typically down the `-z` axis.
