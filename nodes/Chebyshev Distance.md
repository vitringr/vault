---
context:
  - "[[Coordinate System]]"
---

# Chebyshev Distance

Grid distance where the distance between two points equals the greatest difference between them in any coordinate dimension.

```typescript
function getChebyshevDistance(a: Vector2, b: Vector2) {
  const xDifference = a.x - b.x;
  const yDifference = a.y - b.y;
  return Math.max(Math.abs(xDifference), Math.abs(yDifference));
}
```
