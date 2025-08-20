---
tags:
  - "original"
context:
---

#wip

# Battlemage

Does the order matter?

- Unordered: `QQW = QWQ = WQQ`
- Ordered: `QQW ≠ QWQ ≠ WQQ`

| Casts      | Ordered | Unordered |
| ---------- | ------- | --------- |
| **Single** | `3`     | `3`       |
| **Double** | `9`     | `6`       |
| **Triple** | `27`    | `10`      |

Less than 3 elements allowed?

- Three: `QQQ`
- All: `Q, QQ, QQQ`

| Total     | Ordered | Unordered |
| --------- | ------- | --------- |
| **Three** | `27`    | `10`      |
| **All**   | `39`    | `19`      |

All Unordered:

```
[Q] [W] [E]

[QQ] [WW] [EE] [QW] [WE] [EQ]

[QWE] [QQQ] [WWW] [EEE] [QQW] [QQE] [WWQ] [WWE] [EEQ] [EEW]
```

## Four Elements

| Casts      | Ordered | Unordered |
| ---------- | ------- | --------- |
| **Single** | `4`     | `4`       |
| **Double** | `16`    | `10`      |
| **Triple** | ``      | ``        |
