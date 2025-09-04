---
context:
  - "[[Geometry]]"
---

# Distance Formula

Fundamental formula in computational [[Geometry]] that calculates the distances between two points.

---

The distance between points `a` and `b` equals the length of an imaginary line segment that connects them.

## One Dimension

For one dimension, the distance between `a` and `b` equals the absolute of their difference:

`d = abs(a - b)`

Visually, this is the length between the points on the [[Number Line]].

## Two or More Dimensions

For two or more dimensions, a point is a position [[Vector|Vectors]] on a [[Cartesian Coordinate System]].

**Intuition**: In 2D, the take horizontal difference `a.x - b.x` and the vertical difference `a.y - b.y`. Those differences are the sides of an imaginary right triangle. The hypotenuse of this triangle is the line segment connecting the points, and therefore the distance between them.

- This extends to higher dimensions.

Create vector `d` as the difference between `a` and `b`:

`d = b - a`

Calculate the magnitude of vector `d` using the [[Pythagorean Theorem]]:

`||d|| = √(d.x² + d.y²)`

The length between the points equals this magnitude.

## Implementation

```c
typedef struct {
  float x;
  float y;
} Vector;

double getDistance(Vector a, Vector b){
  const float dx = b.x - a.x;
  const float dy = b.y - a.y;
  return sqrt(dx * dx + dy * dy);
}
```

**Always Positive**: Note how there is no need to call for absolute values, as the formula cannot produce negative results by default.

### Squared Distance

Often in computational geometry the exact distance is not needed, for example when comparing distances.

The relatively expensive square root calculation can then be omitted:

```c
double getDistanceSquared(Vector a, Vector b){
  const float dx = b.x - a.x;
  const float dy = b.y - a.y;
  return (dx * dx + dy * dy);
}
```
