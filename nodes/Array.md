---
aliases:
  - Arrays
context:
  - "[[Data Structure]]"
  - "[[Abstract Data Type]]"
---

# Array

Linear [[Data Structure]] containing a collection of elements of the same type in contiguous memory locations.

---

**Indexed**: Array elements can be accessed by their index, usually starting from `0`.

**Contiguous Memory**: Elements are stored in adjacent memory locations.

**Homogeneous**: All array elements are of the same data type.

**Fixed Size**: Arrays have a preallocated fixed size.

## Dimensions

**One-dimensional**: The simplest form of an array is 1D, where `n` number of elements are stored one after another, and are accessed as `array[x]`.

**Multi-dimensional**: An array can contain other arrays, allowing for a more natural presentation of multidimensional data. Such arrays can be accessed as `array[x][y]`, where `x` is the index of a nested array, and `y` is the index of an element inside of it.

This can scale to an arbitrary number of dimensions, although usually not recommended to go beyond 2 or 3 dimensions.

## Performance

**Access**: `O(1)` [[Random Access]] via indices.
