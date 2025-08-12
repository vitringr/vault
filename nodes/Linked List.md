---
context:
  - "[[Data Structure]]"
---

# Linked List

[[Data Structure]] of nodes that are linked together. Each node contains data, as well as a link to the next node.

---

**Node Structure**: `[Data][Link]`

Links can be implemented using [[Pointer|pointers]].

The first node in a linked list is called _head_, and the last node is called _tail_.

## Types

There are different types of linked lists based on their link structure:

- [[Singly Linked List]]
- [[Doubly Linked List]]
- [[Circular Linked List]]

> [!NOTE] It is assumed that _linked list_ refers to _singly linked list_ by default.

## Benefits & Drawbacks

Linked lists are often compared against [[Array|Arrays]].

### Pros

**Independent Storage**: Linked lists allow nodes to be stored wherever there is free space in memory, independent of order.

**Dynamic Capacity**: Linked lists do not have a fixed memory size, since nodes can freely be added or removed from the chain.

**Chain Structure**: When adding or removing nodes, the rest of the nodes in the list do not need to be moved.

### Cons

**No Random Access**: Nodes cannot be accessed directly by [[Random Access]].

**Pointer Memory**: Nodes have to store pointers to other nodes.

## Performance

**Access**: `O(n)`

**Search**: `O(n)`

**Insert/Delete at Head**: `O(1)`

**Insert/Delete at Tail**: Either `O(n)` or `O(1)`, depending on type.
