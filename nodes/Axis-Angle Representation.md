---
context:
  - "[[Rotation]]"
  - "[[Rotation Representation]]"
---

# Axis-Angle Representation

Represents 3D rotation using a [[Unit Vector]] defining the rotation axis and a [[Scalar]] that specifies the rotation angle.

---

Represents any 3D rotation as a pair `(û, θ)`, where:

- **`û`**: Unit vector `(û₁, û₂, û₃)` specifying the rotation axis.
- **`θ`**: Scalar specifying the rotation angle (magnitude).

The rotation vector `w = ûθ` combines both components into a single 3D vector where:

- **Direction** = rotation axis
- **Magnitude** = rotation angle

See [[Euler Rotation Theorem]]

## Properties

Advantages:

**Meaningful**: Axis and angle have clear physical interpretations..

**Minimal**: Uses exactly 3 degrees of freedom (compact storage).

**No Gimbal Lock**: Does not suffer from [[Gimbal Lock]].

Disadvantages:

**Singularity**: At `θ = ±π`, the representation becomes ambiguous.

**Complex Composition**: Combining rotations requires conversion to other forms.

**Non-linear Space**: Not suitable for direct [[Interpolation]].

**Ambiguity**: `(û, θ)` equivalent to `(-û, -θ)`.
