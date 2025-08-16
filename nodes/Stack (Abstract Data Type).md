---
aliases:
  - Stack
context:
  - "[[Abstract Data Type]]"
  - "[[Data Structure]]"
---

# Stack (Abstract Data Type)

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

**By Array**: Uses a fixed size [[Array]] to store elements. A [[Pointer]] to `top` keeps track of the current position.
#wip fast operations; memory efficient; cache-friendly
#wip fixed size; wasted space

**By Linked List**: Uses dynamic [[Linked List]] nodes. The `head` of the linked lists acts as the `top` of the stack.
#wip dynamic size; flexible memory usage
#wip slower than array; extra memory; not cache-friendly

**By Dynamic Array**: #wip
