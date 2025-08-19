---
context:
  - "[[Random Generation]]"
  - "[[Algorithm]]"
---

#wip

# Xorshift

Efficient [[Random Generation]] [[Algorithm]].

---

#wip
shift to the left, scramble with xor, to the right, scramble, etc.

## Intuition

```
00000000000000000000000000101010 // 42
00000000000001010100000000000000 // << 13
00000000000001010100000000101010 // XOR
00000000000000000000000000000010 // >> 17
00000000000001010100000000101000 // XOR
00000000101010000000010100000000 // << 5
00000000101011010100010100101000 // XOR;

Input: 42
Output: 11355432
```

## Implementation

Basic implementation targeted at 32-bit integers:

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
