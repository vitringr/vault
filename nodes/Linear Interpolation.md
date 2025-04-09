---
aliases:
  - lerp
context:
  - "[[Interpolation]]"
---

# Linear Interpolation

[[Interpolation]] method that connects two known points by a straight line. The unknown point is on this line.

---

Algorithm: `A + step * (B - A)`

Imagine a straight line connecting two points (`A` and `B`) in space.

The _step_ number represents a point on that line:

- `0`: Exactly on point `A`.
- `0.5`: Halfway between `A` and `B`.
- `1`: Exactly on point `B`.

**Graph**: [Desmos Visualization](https://www.desmos.com/calculator/3qqhmusbzi)

## Dimensions

**1 Dimension**: If the two inputs are 1D [[Scalar|scalars]] - imagine them on the 1D [[Number Line]].

**2 Dimensions**: Known as [[Bilinear Interpolation]]. If the two inputs are 2D points ([[Vector|vectors]]) in a [[Coordinate System]] - imagine a straight line connecting them.

**3 Dimensions**: The same, but imagine the line connecting points in 3D space.

## Implementation

```typescript
// 1 Dimension:
function lerp(a: number, b: number, step: number) {
  return a + step * (b - a);
}

// 2 Dimensions:
function lerp(va: Vector2, v2: Vector2, step: number) {
  return new Vector2(
    va.x + step * (v2.x - va.x),
    va.y + step * (v2.y - va.y)
  );
}

// 3 Dimensions:
function lerp(va: Vector3, v2: Vector3, step: number) {
  return new Vector3(
    va.x + step * (v2.x - va.x),
    va.y + step * (v2.y - va.y),
    va.z + step * (v2.z - va.z)
  );
}
```
