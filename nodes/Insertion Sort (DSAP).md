---
context:
  - "[[DSAP]]"
---

# Insertion Sort (DSAP)

Implement [[Insertion Sort]].

---

**Difficulty**: Easy
**Time Complexity**: `O(n²)` Quadratic
**Space Complexity**: `O(1)` Constant

```c
void insertionSort(int arr[], int size) {
  for (int i = 1; i < size; i++) {
    int current = arr[i];
    int k = i - 1;

    while (k >= 0 && arr[k] > current) {
      arr[k + 1] = arr[k];
      k--;
    }

    arr[k + 1] = current;
  }
}
```
