---
context:
  - "[[Data Structure]]"
---

#wip

# Linked List

[[Data Structure]] of nodes that are linked together. Each node contains data, as well as a link to the next node.

---

Links can be implemented using [[Pointer|pointers]].

Linked lists are often compared versus [[Array|Arrays]].

## Benefits

**Independent Storage**: Linked lists allow nodes to be stored wherever there is free space in memory, independent of order.

**Dynamic Capacity**: Linked lists do not have a fixed memory size, since nodes can freely be added or removed from the chain.

**Chain Structure**: When adding or removing nodes, the rest of the nodes in the list do not need to be moved.

## Drawbacks

**No Random Access**: Nodes cannot be accessed directly by [[Random Access]].

**Pointer Memory**: Nodes have to store pointers to other nodes.
