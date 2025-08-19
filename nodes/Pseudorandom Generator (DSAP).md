---
context:
  - "[[DSAP]]"
---

# Pseudorandom Generator (DSAP)

Build [[Pseudorandom]] [[RNG|Random Number Generation]].

---

**Difficulty**: Medium

## Implementation

Implementation using [[Xorshift]]:

```c
unsigned int state = 1;

int xorshift() {
  state ^= state << 13;
  state ^= state >> 17;
  state ^= state << 5;
  return state;
}
```

