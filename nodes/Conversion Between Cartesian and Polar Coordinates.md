---
context:
  - "[[Cartesian Coordinate System]]"
  - "[[Polar Coordinate System]]"
---

#wip

# Conversion Between Cartesian and Polar Coordinates

ad

---

Polar to Cartesian:

```
x = cos(θ) * r
y = sin(θ) * r
```

Cartesian to Polar:

```
r = √(x² + y²)
θ = atan2(y, x)
```

## Implementation

> [!WARNING] Undefined Origin
> Note that in some software libraries `atan2` is undefined at the origin where `x == 0` and `y == 0`. Make sure to check and handle this case.
