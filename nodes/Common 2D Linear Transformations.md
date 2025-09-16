---
tags:
  - "data"
context:
  - "[[Linear Transformation]]"
---

# Common 2D Linear Transformations

Standard 2D space [[Linear Transformation]] [[Matrix]] list.

---

#wip

## Identity matrix

Right remains right, up remains up.

```
┌────┬────┐
│  1 │  0 │
├────┼────┤
│  0 │  1 │
└────┴────┘
```

## Reflection in the `𝑦`-axis

Right has become left, up remains up.

```
┌────┬────┐
│ -1 │  0 │
├────┼────┤
│  0 │  1 │
└────┴────┘
```

## Reflection in the `𝑥`-axis

Right remains right, up has become down.

```
┌────┬────┐
│  1 │  0 │
├────┼────┤
│  0 │ -1 │
└────┴────┘
```

## Rotation by `180°`

Right has become left, up has become down.

```
┌────┬────┐
│ -1 │  0 │
├────┼────┤
│  0 │ -1 │
└────┴────┘
```

## Reflection in the line `𝑦 = 𝑥`

Right has become up, up has become right.

```
┌────┬────┐
│  0 │  1 │
├────┼────┤
│  1 │  0 │
└────┴────┘
```

## Rotation by `90°` anticlockwise

Right has become up, up has become left.

```
┌────┬────┐
│  0 │ -1 │
├────┼────┤
│  1 │  0 │
└────┴────┘
```

## Rotation by `90°` clockwise

Right has become down, up has become right.

```
┌────┬────┐
│  0 │  1 │
├────┼────┤
│ -1 │  0 │
└────┴────┘
```

## Reflection in the line `𝑦 = −𝑥`

Right has become down, up has become left.

```
┌────┬────┐
│  0 │ -1 │
├────┼────┤
│ -1 │  0 │
└────┴────┘
```

## Scaling by scale factor `𝑎` in the `𝑥` direction

Right is multiplied by `a`, up remains up.

```
┌────┬────┐
│  a │  0 │
├────┼────┤
│  0 │  1 │
└────┴────┘
```

## Scaling by scale factor `𝑎` in the `𝑦` direction

Right remains right, up is multiplied by `a`.

```
┌────┬────┐
│  1 │  0 │
├────┼────┤
│  0 │  a │
└────┴────┘
```

## Scaling by scale factor `𝑎` from the origin

Right is multiplied by `a`, up is multiplied by `a`.

```
┌────┬────┐
│  a │  0 │
├────┼────┤
│  0 │  a │
└────┴────┘
```

## Scaling by scale factor `𝑎` for `𝑥` and `b` for `y`

Right is multiplied by `a`, up is multiplied by `b`.

```
┌────┬────┐
│  a │  0 │
├────┼────┤
│  0 │  b │
└────┴────┘
```
