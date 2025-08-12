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

_Probably the simplest and most universal data structure._

**Indexed**: Array elements can be accessed by their index, usually starting from `0`.

**Contiguous Memory**: Elements are stored in adjacent memory locations.

**Homogeneous**: All array elements are of the same data type.

**Fixed Size**: Arrays have a preallocated fixed size.

## Dimensions

**One-dimensional**: The simplest form of an array is 1D, where `n` number of elements are stored one after another, and are accessed as `array[x]`.

**Multi-dimensional**: An array can contain other arrays, allowing for a more natural presentation of multidimensional data. Such arrays can be accessed as `array[x][y]`, where `x` is the index of a nested array, and `y` is the index of an element inside of it.

This can scale to an arbitrary number of dimensions, although usually not recommended to go beyond 2 or 3 dimensions.

## Benefits & Drawbacks

It's all about the memory layout.

Since array elements are stored in contiguous memory locations and are of the same size, it is easy to predict where an element should be, given only a [[Pointer]] to the start (head) of the array. But this also comes at the cost of making the array less dynamic than other data structures.

### Pros

**Random Access**: Efficient [[Random Access]] for all array elements.

**Memory Efficiency**: Elements are only the raw data itself. They do not need to store any metadata related to their layout in memory.

**Predictable**: Arrays are predefined in memory and therefore predictable.

### Cons

**Fixed Size**: The size of an array cannot be changed.

**Homogeneous**: Arrays cannot contain different types of elements.

## Performance

**Access**: `O(1)`

**Search**: `O(n)` for unsorted arrays.
