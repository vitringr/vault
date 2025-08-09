---
context:
  - "[[Sorting Algorithm]]"
---

# Counting Sort

Stable [[Sorting Algorithm]] that counts the occurrence frequency of elements in a collection.

---

Given a collection of elements, the algorithm finds the range (min - max) `k` elements in the collection. It then counts the occurrences of each element, and later uses them to reconstruct a sorted collection.

Optimal for small `k` integer ranges.

## Computational Complexity

The performance of counting sort depends on `k`, or compared to other sorting algorithms, on the ratio `n / k`.

For low ranges of `k`, counting sort can be extremely efficient.

**Time Complexity**: `O(n + k)`
**Space Complexity**: `O(n + k)`

## Implementation

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

  // Count frequencies
  for (const num of arr) {
    count[num - min]++;
  }

  // Cumulative counts
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

**Cumulative counts**: So that every unique (`k` range) element knows how many elements are before it, therefore knowing which position it should start from.
