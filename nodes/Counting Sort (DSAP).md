---
context:
  - "[[DSAP]]"
---

# Counting Sort (DSAP)

Implement [[Counting Sort]].

---

**Difficulty**: Medium

**Time Complexity**: `O(n + k)`
**Space Complexity**: `O(n + k)`

```javascript
function countingSort(arr) {
  if (arr.length <= 1) return arr;

  let min = arr[0];
  let max = arr[0];
  for (const num of arr) {
    if (num < min) min = num;
    if (num > max) max = num;
  }

  const range = max - min + 1;
  const count = new Array(range).fill(0);
  const output = new Array(arr.length);

  for (const num of arr) {
    count[num - min]++;
  }

  for (let i = 1; i < range; i++) {
    count[i] += count[i - 1];
  }

  for (let i = arr.length - 1; i >= 0; i--) {
    output[count[arr[i] - min] - 1] = arr[i];
    count[arr[i] - min]--;
  }

  return output;
}
```
