---
aliases:
  - Abstract Data Types
  - ADT
context:
  - "[[Data Type (Computer Science)]]"
---

# Abstract Data Type

Logical model of a [[Data Structure]].

---

Defines the logical properties and behavior of a data structure, independent of actual implementation.

Focuses on _what_ the data does instead of _how_ it does it.

## Benefits

Benefits of using theoretical models:

**Abstraction**: Hides away implementation details.

**Encapsulation**: Exposes only the [[Interface]], not internal data representation.

**Reusability**: The same ADTs can be reused across different systems, independent of implementation.

**Theoretical Foundation**: Enables formal mathematical analysis.

## Common Abstract Data Types

| ADT                            | Core Operations                     | Possible Implementations               |
| ------------------------------ | ----------------------------------- | -------------------------------------- |
| [[Stack (Abstract Data Type)]] | `push()`, `pop()`, `peek()`         | [[Array]], [[Linked List]]             |
| [[Queue]]                      | `enqueue()`, `dequeue()`, `front()` | [[Array]], [[Linked List]], [[Heap]]   |
| [[List]]                       | `add()`, `remove()`, `get()`        | [[Array]], [[Linked List]]             |
| [[Map]]                        | `put(key, value)`, `get(key)`       | [[Hash Table]], [[Binary Search Tree]] |
