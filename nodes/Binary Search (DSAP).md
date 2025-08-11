---
context:
  - "[[DSAP]]"
---

# Binary Search (DSAP)

Implement [[Binary Search]].

---

**Difficulty**: Basic

**Time Complexity**: `O(log n)`
**Space Complexity**: `O(1)`

```c
int binarySearch(int *arr, int size, int target) {
  int left = 0;
  int right = size - 1;

  while (left <= right) {
    int mid = left + ((right - left) >> 1);

    if (arr[mid] == target)
      return mid;

    if (target < arr[mid])
      right = mid - 1;
    else
      left = mid + 1;
  }

  return -1;
}
```
