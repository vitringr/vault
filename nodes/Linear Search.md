---
aliases:
  - Sequential Search
context:
  - "[[Search Algorithm]]"
---

# Linear Search

Sequentially checks each element of a [[List]] or [[Array]] until it finds the target or reaches the end.

---

Works on both sorted and unsorted collections.

## Computational Complexity

The performance depends on where the target is.

**Time Complexity**:

- Best: `O(1)` when the target is the first element.
- Average: `O(n/2)` ≈ `O(n)`
- Worst: `O(n)`

**Space Complexity**: `O(1)`

## Implementation

```c
int linearSearch(int arr[], int size, int target) {
  for(int i = 0; i < size; i++) {
    if(arr[i] == target) return i;
  }
  return -1;
}
```
