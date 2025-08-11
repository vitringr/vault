---
context:
  - "[[Search Algorithm]]"
---

# Binary Search

Repeatedly divides a sorted collection in half to find a target.

---

Compares the target value to the middle element value after each division to see if it matches, or if the value is lower or higher.

## Computational Complexity

**Time Complexity**: `O(log n)`

**Space Complexity**: `O(1)`

## Implementation

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

Note that the `>>` is only for efficiency.

Note that `left + (right - left) / 2` is safer than `(left + right) / 2` as it could prevent overflows.
