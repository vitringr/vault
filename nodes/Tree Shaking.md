---
context:
  - "[[Dead Code Elimination]]"
---

# Tree Shaking

[[Dead Code Elimination]] technique applied when optimizing code.

---

Described as "_live code inclusion_".

Eliminates unused functions from across the bundle by starting at the entry point and only including functions that may be executed.

> Sometimes you have to add an entire library even if you only need it for a few functions, but thanks to tree shaking the program can only include the individual functions needed from that library.
