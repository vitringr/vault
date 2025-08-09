---
context:
  - "[[DSAP]]"
---

# Linear Search (DSAP)

Implement [[Linear Search]].

---

**Difficulty**: Basic

**Time Complexity**: `O(n)`
**Space Complexity**: `O(1)`

```c
int linearSearch(int arr[], int size, int target) {
  for(int i = 0; i < size; i++) {
    if(arr[i] == target) return i;
  }
  return -1;
}
```
