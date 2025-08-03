---
context:
  - "[[Sorting Algorithm]]"
---

# Bubble Sort

Stable [[Sorting Algorithm]] that repeatedly iterates through the collection, comparing adjacent elements, and swapping them if needed.

---

**Name**: Gets its name because with each iteration the largest element "bubbles" up to its proper location.

## Computational Complexity

Bubble sort is simple, but very inefficient for large collections.

**Time Complexity**: `O(n²)` Polynomial
**Space Complexity**: `O(1)` Constant

## Implementation

```c
void bubbleSort(int arr[], int size) {
  for (int i = 0; i < size - 1; i++) {
    int swapped = 0;
    for (int k = 0; k < size - 1 - i; k++) {
      if (arr[k] > arr[k + 1]) {
        int temp = arr[k];
        arr[k] = arr[k + 1];
        arr[k + 1] = temp;
        swapped = 1;
      }
    }
    if(!swapped) break;
  }
}
```
