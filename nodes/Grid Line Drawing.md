---
context:
  - "[[Programming]]"
  - "[[Lattice]]"
---

# Grid Line Drawing

Method to programatically drawing lines on a rectangular grid.

---

Given two cells, `A` and `B`, calculate the [[Chebyshev Distance]] between them. Use this distance to perform [[Linear Interpolation]] between the two cells, generating an array of points along the line. Finally, round the coordinates of these points.

## Implementation

```typescript
function getChebyshevDistance(a: Vector2, b: Vector2) {
  const xDifference = a.x - b.x;
  const yDifference = a.y - b.y;
  return Math.max(Math.abs(xDifference), Math.abs(yDifference));
}

function getLine(a: Vector2, b: Vector2, steps: number) {
  const linePoints: Vector2[] = [];

  const step = 1 / steps;

  for (let i = 1; i < steps; i++) {
    const point = Vector2.lerp(a, b, step * i).round();
    linePoints.push(point);
  }

  return linePoints;
}
```
