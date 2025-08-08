---
context:
  - "[[DSAP]]"
---

# Bubble Sort (DSAP)

Implement [[Bubble Sort]].

---

**Difficulty**: Easy
**Time Complexity**: `O(n²)` Quadratic
**Space Complexity**: `O(1)` Constant

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
