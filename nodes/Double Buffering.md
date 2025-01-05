---
aliases:
  - "Ping-Pong Rendering"
context:
  - "[[Programming]]"
  - "[[Computing]]"
---

# Double Buffering

Technique where two [[Data Buffer|Data Buffers]] are used to continuously store and update data by swapping each other.

1. The _Front Buffer_ uses the current data.
2. New data is written to the _Back Buffer_.
3. The buffers are swapped.

---

Commonly used in [[Computer Graphics]].

