---
context:
  - "[[Abstract Data Type]]"
---

# Queue

Linear collection of elements using FIFO (First In First Out) operations.

---

**Sequential**: Elements are stored in a sequence, preserving the order they were added.

**Operations**: The queue can be modified by the addition of entities at one end, or the removal of entities from the other end.

- `enqueue(x)`: Add to rear.
- `dequeue`: Remove from front.
- `peek`: Inspect front item.

**Time Complexity**: `O(1)` for `enqueue`/`dequeue`.
