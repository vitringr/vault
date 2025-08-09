---
context:
  - "[[DSAP]]"
---

# Quicksort (DSAP)

Implement [[Quicksort]].

---

**Difficulty**: Medium

**Time Complexity**: From `O(n log n)` to `O(n²)`
**Space Complexity**: From `O(log n)` to `O(n)`

```c
int partition(int arr[], int start, int end) {
  int pivot = arr[start];
  int left = start - 1;
  int right = end + 1;

  while (1) {
    while (arr[++left] < pivot);
    while (arr[--right] > pivot);

    if (left >= right)
      return right;

    int temp = arr[left];
    arr[left] = arr[right];
    arr[right] = temp;
  }
}

void quickSort(int arr[], int low, int high) {
  if (low < high) {

    int pi = partition(arr, low, high);

    quickSort(arr, low, pi);
    quickSort(arr, pi + 1, high);
  }
}
```
