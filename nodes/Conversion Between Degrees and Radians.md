---
tags:
  - "data"
context:
  - "[[Mathematics]]"
---

# Conversion Between Degrees and Radians

One degree measures `1/360` of a circle.

One radian is the angle subtended at the center of a circle by an arc whose length is equal to the radius of the circle.

The circumference of a circle is `τ`, or `2π`.

`1 rad  = (360 / τ)º       ≈ 57.29578`
`1º     = (τ / 360) rad    ≈ 0.017453`

```c
#define TAU 6.2831853071

double degreesToRadians(double degrees) {
  return degrees * (TAU / 360);
}

double radiansToDegrees(double radians) {
  return radians * (360 / TAU);
}
```
