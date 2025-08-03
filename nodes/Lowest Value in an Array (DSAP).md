---
context:
  - "[[DSAP]]"
---

# Lowest Value in an Array (DSAP)

Given an [[Array]], output the element with the lowest value.

---

**Difficulty**: Basic
**Time Complexity**: `0(n)` Linear
**Space Complexity**: `0(1)` Constant

```c
int getLowest(int arr[], int size) {
  int lowest = arr[0];

  for (int i = 0; i < size; i++) {
    if (arr[i] < lowest) {
      lowest = arr[i];
    }
  }

  return lowest;
}
```
