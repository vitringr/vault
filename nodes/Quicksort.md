---
context:
  - "[[Sorting Algorithm]]"
---

#wip

# Quicksort

Efficient unstable [[Sorting Algorithm]] that uses [[Recursion]] and the [[Divide and Conquer]] strategy.

---

1. Choose a "pivot" element from the collection.
2. Partition the collection into two sub-collections using the pivot.
3. Recursively sort the sub-collections.

## Variations

The Quicksort algorithm has different variations which affect performance and worst-case behavior.

### Pivot Choice

The choice of pivot significantly impacts efficiency. Common strategies include:

**Middle Element**: Simply picks the middle element.
**First/Last Element**: Simple implementation, but risks worst-case `O(n²)` on sorted or nearly sorted data.
**Median-of-Three**: Picks the median of the first, middle, and last elements to balance partitions.
**Random Pivot**: Randomly selects an element, reducing worst-case probability.

### Partition Scheme

The core of Quicksort lies in partitioning. There are two common approaches:

**Lomuto Partition**: Pivot is usually the last element. Iterates through the array, swapping elements less than the pivot, finally placing the pivot in its correct position.

- Simpler to understand and implement.
- Inefficient compared to Hoare partition.

**Hoare Partition**: Pivot is usually the first or middle element. Uses two pointers starting at both ends, moving inward until they cross, swapping misplaced elements in the process.

- Trickier to understand and implement.
- Fewer swaps than Lomuto partition.

### Tail-recursive

The key idea is to recurse only on the smaller partition and iterate on the larger one. This ensures the recursion depth never exceeds `O(log n)`.

### Hybrid & Adaptive

Hybrid approaches combine Quicksort with other algorithms to optimize performance adaptively, switching strategies based on input characteristics.

For example, the algorithm can switch to something like [[Insertion Sort]] when the collection size is less than a given threshold.

## Computational Complexity

As the name implies, Quicksort, on average, is one of the fastest sorting algorithms.

**Time Complexity**:

- Best: `O(n log n)`
- Average: `O(n log n)`
- Worst: `O(n²)`

**Space Complexity**:

- Best: `O(log n)`
- Average: `O(log n)`
- Worst: `O(n)`

## Implementation
