---
context:
  - "[[Vector]]"
---

# Vector Normalization

To normalize a [[Vector]], divide each of its components by its magnitude.

---

To calculate the magnitude vector `v`, use the [[Pythagorean Theorem]]:

```
v.x² + v.y² = v.magnitude²

v.magnitude = √(v.x² + v.y²)
```

To produce the normalized vector `n`, divide the components of `v` by the magnitude:

```
n.x = v.x / v.magnitude
n.y = v.y / v.magnitude
```

The result is a unit vector that points in the same direction.

## Implementation

```c
void normalize(Vector *v) {
  const float magnitude = sqrt(v->x * v->x + v->y * v->y);
  if (magnitude == 0)
    return;

  v->x /= magnitude;
  v->y /= magnitude;
}
```
