---
aliases:
  - Arrays
context:
  - "[[Data Structure]]"
  - "[[Abstract Data Type]]"
---

# Array

Fixed-size [[Data Structure]] containing a collection of elements of the same type, indexed sequentially.

---

**Access**: `O(1)` access via indices.

**Fixed Size**: Arrays have a preallocated fixed size.

**Homogeneous**: All array elements are of the same data type.

## Dimensions

**Single**: The simplest form of an array is 1D, where `n` number of elements are stored one after another, and are accessed as `array[x]`.

**Multiple**: An array can contain other arrays, allowing for a more natural presentation of multidimensional data. Such arrays can be accessed as `array[x][y]`, where `x` is the index of a nested array, and `y` is the index of an element inside of it.

This can scale to an arbitrary number of dimensions.
