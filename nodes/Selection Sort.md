---
context:
  - "[[Sorting Algorithm]]"
---

# Selection Sort

Unstable [[Sorting Algorithm]] that repeatedly moves the next lowest value to the sorted front part of the collection.

---

## Computational Complexity

**Time Complexity**: `O(n²)` Quadratic
**Space Complexity**: `O(1)` Constant

## Implementation

```c
void selectionSort(int arr[], int size) {
  for (int i = 0; i < size - 1; i++) {
    int min = i;
    for (int k = i + 1; k < size; k++) {
      if (arr[k] < arr[min]) {
        min = k;
      }
    }

    if (min != i) {
      int temp = arr[i];
      arr[i] = arr[min];
      arr[min] = temp;
    }
  }
}
```
