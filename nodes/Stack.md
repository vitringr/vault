---
context:
  - "[[Abstract Data Type]]"
  - "[[Data Structure]]"
---

# Stack

Linear collection of elements using LIFO (Last In First Out) operations.

---

The last added element is the first that is removed.

## Operations

Core stack operations:

- **Push**: Add new element on top.
- **Pop**: Remove and return the top element.
- **Peek**: Return the top element.
- **IsEmpty**: Check if the stack is empty.
- **Size**: Get the number of elements.

## Performance

**Time Complexity**: `O(1)` for all core operations.

**Space Complexity**: `O(n)`

## Implementation

Stacks can be implemented in multiple ways.

### By Array

Uses a fixed size [[Array]] to store elements. A [[Pointer]] to `top` keeps track of the current position.

**Pros**: Fast operations, memory efficient, cache-friendly.
**Cons**: Fixed size, wasted space.

## By Linked List

Uses dynamic [[Linked List]] nodes. The `head` of the linked lists acts as the `top` of the stack.

**Pros**: Dynamic size, flexible memory usage.
**Cons**: Slower than array, extra memory, not cache-friendly.

## By Dynamic Array

Uses a [[Dynamic Array]], combining the benefits of array-based stacks with the flexibility of dynamic sizing.

**Pros**: No fixed capacity, amortized `O(1)` time, cache-friendly.
**Cons**: Occasional resizing overhead, potential memory waste.
