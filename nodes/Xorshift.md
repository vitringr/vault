---
context:
  - "[[Random Generation]]"
  - "[[Algorithm]]"
---

# Xorshift

Efficient [[Random Generation]] [[Algorithm]].

---

The algorithm shifts the bits of the number, and then does XOR between the old number and the shifted one. This is repeated a few times, producing good pseudorandom values.

```
Input: 42

00000000000000000000000000101010 // 42
00000000000001010100000000000000 // << 13
00000000000001010100000000101010 // XOR
00000000000000000000000000000010 // >> 17
00000000000001010100000000101000 // XOR
00000000101010000000010100000000 // << 5
00000000101011010100010100101000 // XOR;

Output: 11355432
```

## Implementation

Basic implementation targeted for 32-bit integers:

```c
int xorshift() {
  state ^= state << 13;
  state ^= state >> 17;
  state ^= state << 5;
  return state;
}
```

Implementation for floating-point values in the `0` to `1` range:

```c
float random01() {
  state ^= state << 13;
  state ^= state >> 17;
  state ^= state << 5;
  return (float)state / 4294967295.0f;
}
```

Optimized variant of the floating-point `0` to `1` range:

```c
#define SCALE_FACTOR (1.0 / (float)UINT32_MAX)

static inline float random01() {
  state ^= state << 13;
  state ^= state >> 17;
  state ^= state << 5;
  return state * SCALE_FACTOR;
}
```
