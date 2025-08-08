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

The key process in quicksort is partitioning.

**Lomuto Partition**:

**Hoare Partition**:

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
