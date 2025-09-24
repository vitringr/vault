---
tags:
  - "data"
context:
  - "[[Linear Transformation]]"
  - "[[Matrix]]"
---

# Common Linear Transformations Matrices

Collection of common linear transformations matrices.

---

Each transformation is defined by where it sends the standard basis vectors, `î = <1, 0>` and `ĵ = <0, 1>`. The resulting vectors become the columns of the matrix.

## Identity

Right remains right, up remains up.

```
┌───┬───┐
│ 1 │ 0 │
├───┼───┤
│ 0 │ 1 │
└───┴───┘
```

## Reflection

### `𝑦`-axis

Right has become left, up remains up.

```
┌────┬───┐
│ -1 │ 0 │
├────┼───┤
│  0 │ 1 │
└────┴───┘
```

### `𝑥`-axis

Right remains right, up has become down.

```
┌───┬────┐
│ 1 │  0 │
├───┼────┤
│ 0 │ -1 │
└───┴────┘
```

### `𝑦 = 𝑥` line

Right has become up, up has become right.

```
┌───┬───┐
│ 0 │ 1 │
├───┼───┤
│ 1 │ 0 │
└───┴───┘
```

### `𝑦 = −𝑥` line

Right has become down, up has become left.

```
┌────┬────┐
│  0 │ -1 │
├────┼────┤
│ -1 │  0 │
└────┴────┘
```

## Rotation

### `180°` turn

Right has become left, up has become down.

```
┌────┬────┐
│ -1 │  0 │
├────┼────┤
│  0 │ -1 │
└────┴────┘
```

### `90°` clockwise

Right has become down, up has become right.

```
┌────┬───┐
│  0 │ 1 │
├────┼───┤
│ -1 │ 0 │
└────┴───┘
```

### `90°` counterclockwise

Right has become up, up has become left.

```
┌───┬────┐
│ 0 │ -1 │
├───┼────┤
│ 1 │  0 │
└───┴────┘
```

## Scaling

### Factor `𝑎` in the `𝑥` direction

Right is multiplied by `a`, up remains up.

```
┌───┬───┐
│ a │ 0 │
├───┼───┤
│ 0 │ 1 │
└───┴───┘
```

### Factor `𝑎` in the `𝑦` direction

Right remains right, up is multiplied by `a`.

```
┌───┬───┐
│ 1 │ 0 │
├───┼───┤
│ 0 │ a │
└───┴───┘
```

### Factor `𝑎` from the origin

Right is multiplied by `a`, up is multiplied by `a`.

```
┌───┬───┐
│ a │ 0 │
├───┼───┤
│ 0 │ a │
└───┴───┘
```

### Factor `𝑎` for `𝑥` and `b` for `y`

Right is multiplied by `a`, up is multiplied by `b`.

```
┌───┬───┐
│ a │ 0 │
├───┼───┤
│ 0 │ b │
└───┴───┘
```
