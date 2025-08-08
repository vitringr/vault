---
context:
  - "[[Sorting Algorithm]]"
---

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

- **Middle Element**: Simply picks the middle element.
- **First/Last Element**: Simple implementation, but risks worst-case `O(n²)` on sorted or nearly sorted data.
- **Median-of-Three**: Picks the median of the first, middle, and last elements to balance partitions.
- **Random Pivot**: Randomly selects an element, reducing worst-case probability.

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

This implementation is _tail recursive_ with _hoare partitioning_, _middle element pivot_, and _insertion sort fallback_.

```c
static inline void swap(int *a, int *b) {
  int temp = *a;
  *a = *b;
  *b = temp;
}

static void insertionSort(int *arr, int low, int high) {
  for (int i = low + 1; i <= high; i++) {
    int key = arr[i];
    int k = i - 1;
    while (k >= low && arr[k] > key) {
      arr[k + 1] = arr[k];
      k--;
    }
    arr[k + 1] = key;
  }
}

static int partition(int *arr, int start, int end) {
  const int pivot = arr[start + (end - start) / 2];

  int left = start - 1;
  int right = end + 1;

  while (1) {
    while (arr[++left] < pivot);
    while (arr[--right] > pivot);

    if (left >= right)
      return right;

    swap(&arr[left], &arr[right]);
  }
}

void quicksort(int *arr, int start, int end) {
  if (end - start <= 20) {
    insertionSort(arr, start, end);
    return;
  }

  while (start < end) {
    int p = partition(arr, start, end);

    if (p - start < end - p) {
      quicksort(arr, start, p);
      start = p + 1;
    } else {
      quicksort(arr, p + 1, end);
      end = p;
    }
  }
}

void sort(int *arr, int size) {
  if (size <= 1)
    return;
  quicksort(arr, 0, size - 1);
}
```
