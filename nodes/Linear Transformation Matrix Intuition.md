---
context:
  - "[[Linear Algebra]]"
  - "[[Linear Transformation]]"
---

# Linear Transformation Matrix Intuition

Intuition to how a [[Linear Transformation]] works, how it affects the [[Basis Vectors]] of a [[Coordinate System]], how this change gets reflected on every [[Vector]] in the system, and how to describe such transformation using a [[Matrix]].

---

Linear maps are completely defined by how they affect the basis vectors. The matrix is a convenient package for that information.

## Transformation

Imagine every vector as a scaling of the basis vectors `i` and `j`.

- By default, vector `i` (horizontal) equals `<1, 0>`.
- By default, vector `j` (vertical) equals `<0, 1>`.

Any vector's coordinates `<x, y>` are the instructions: "go `x` units in the `i` direction and `y` units in the `j` direction".

The scale of `i` determines the horizontal direction, and the scale of `j` determines the vertical direction.

- The origin `<0, 0>` is at `0i + 0j`: `0<1, 0> + 0<0, 1>` ⇒ `<0, 0> + <0, 0>` ⇒ `<0, 0>`
- The vector `<1, 1>` is at `1i + 1j`: `1<1, 0> + 1<0, 1>` ⇒ `<1, 0> + <0, 1>` ⇒ `<1, 1>`
- The vector `<3, 0>` is at `3i + 0j`: `3<1, 0> + 0<0, 1>` ⇒ `<3, 0> + <0, 0>` ⇒ `<3, 0>`
- The vector `<1, -2>` is at `1i + (-2j)`: `1<1, 0> + (-2<0, 1>)` ⇒ `<1, 0> - <0, 2>` ⇒ `<1, -2>`

Any vector `<x, y>` can be described as `xi + yj`.

- `xi + xj` ⇒ `x<1, 0> + y<0, 1>` ⇒ `<x, 0> + <0, y>` ⇒ `<x, y>`

When there is no transformation, `i` is `<1, 0>` and `j` is `<0, 1>`.

After a linear Transformation, the position of the basis vectors `i` and `j` can change.

Imagine a scaling of two, where `i` is now equal to `<2, 0>`, and `j` is now equal to `<0, 2>`.

Any vector will adapt the new transformation by being a scaling of the new basis vectors `i` and `j`:

- The origin `<0, 0>` is at `0i + 0j`: `0<2, 0> + 0<0, 2>` ⇒ `<0, 0> + <0, 0>` ⇒ `<0, 0>`
- The vector `<1, 1>` is at `1i + 1j`: `1<2, 0> + 1<0, 2>` ⇒ `<2, 0> + <0, 2>` ⇒ `<2, 2>`
- The vector `<3, 0>` is at `3i + 0j`: `3<2, 0> + 0<0, 2>` ⇒ `<6, 0> + <0, 0>` ⇒ `<6, 0>`
- The vector `<1, -2>` is at `1i + (-2j)`: `1<2, 0> + (-2<0, 2>)` ⇒ `<2, 0> - <0, 4>` ⇒ `<2, -4>`

The basis vectors `i` and `j` change the whole coordinate system, and all the other vectors (`<x, y>` ⇔ `xi + yj`) adapt to that change.

The place where a `<x, y>` vector lands will be `x` times the transformed version of `i`, plus `y` times the transformed version of `j`.

## Matrix

The matrix is a concise way to describe a linear transformation.

It simply records the new positions of the basis vectors `i` and `j`:

- The **first column** equals the first basis vector `i`.
- The **second column** equals the second basis vector `j`.

For example, in the identity matrix:

```
┌───┬───┐
│ 1 │ 0 │
├───┼───┤
│ 0 │ 1 │
└───┴───┘
```

- the basis vector `i` remains at `x: 1, y: 0`
- the basis vector `j` remains at `x: 0, y: 1`.

The convention for any matrix `[a, b, c, d]` is that:

- `a` and `c` are the `x` and `y` components of the `i` basis vector.
- `b` and `d` are the `x` and `y` components of the `j` basis vector.

So any vector `<x, y>` that is multiplied by a matrix `[a, b, c, d]` follows the pattern:

```
 ┌───┐   ┌───┬───┐       ┌───┐       ┌───┐
 │ x │   │ a │ b │       │ a │       │ b │
 ├───┤ * ├───┼───┤ = x * ├───┤ + y * ├───┤ = <xa, xc> + <yb, yd>
 │ y │   │ c │ d │       │ c │       │ d │
 └───┘   └───┴───┘       └───┘       └───┘
```

See [[Common 2D Linear Transformations]]
