---
context:
  - "[[C (Programming Language)]]"
  - "[[Random Generation]]"
---

# C Random Generation

Random generation in the C programming language.

---

## Default Implementation

The language provides built-in `rand()` and `srand()` functions, defined in `<stdlib.h>`.

- Extremely performant.
- Poor randomness.
- Very portable.

There are also `random()` and `srandom()` which are superior, but not as portable as `rand()`.

- Extremely performant.
- Good randomness.
- Lower portability.

## Custom Implementation

Implementation using [[Xorshift]]:

```c
#include <stdint.h>

static uint32_t state = 1;

void seed_rng(uint32_t seed) { state = seed ? seed : 1; }

#define SCALE_FACTOR (1.0 / (float)UINT32_MAX)

static inline float random01() {
  state ^= state << 13;
  state ^= state >> 17;
  state ^= state << 5;
  return state * SCALE_FACTOR;
}
```

Returns pseudorandom floating-point values in the `0` to `1` range.

## Best Practices

**Always Seed**: Don't rely on the default seed. Always seed the random functions before use.

**Seed Only Once**: Seeding multiple times (inside a loop for example) can destroy the randomness.

**Avoid Modulo Bias**: Using `rand() % N` introduces unwanted bias.
