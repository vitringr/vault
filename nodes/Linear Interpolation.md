---
aliases:
  - lerp
context:
  - "[[Interpolation]]"
---

# Linear Interpolation

[[Interpolation]] method that connects two known points by a straight line. The unknown point is on this line.

---

Implementation:

```typescript
function lerp(a: number, b: number, step: number) {
  return a + step * (b - a);
}
```

**Step**: The _step_ number represents a point on the line:

- `0`: Exactly on point `A`.
- `0.5`: Halfway between `A` and `B`.
- `1`: Exactly on point `B`.

## Intuition

Imagine a straight line connecting two points (`A` and `B`) in space.

[Desmos Visualization](https://www.desmos.com/calculator/3qqhmusbzi)

### Dimensions

**1 Dimension**: If the two numbers are 1D scalars [[Scalar|scalars]] - imagine them on the 1D [[Number Line]].

**2 Dimensions**: If the two numbers are 2D points in a [[Coordinate System]] - imagine a straight line connecting them.

**3 Dimensions**: The same, but imagine the line connecting points in 3D space.
