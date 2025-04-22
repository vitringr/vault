---
context:
  - "[[JavaScript]]"
---

# JavaScript Keyed Collections

JavaScript data collections indexed by a key.

---

## Map

Collection of key-value pairs that can iterate its elements in insertion order.

See [[Map]]

## WeakMap

Map whose keys must be objects that can get garbage collected.

The references to the objects are _weak_, meaning garbage collection is not prevented, and can collect those objects.

## Set

Collection of unique values.

See [[Set (Abstract Data Type)|Set]]

## WeakSet

Collection of objects or symbols that can get garbage collected.

The references to the objects are held _weakly_. If there is no other reference to an object stored in the `WeakSet`, they can be garbage collected.
