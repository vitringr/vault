---
context:
  - "[[DSAP]]"
---

# Output Binary Form (DSAP)

Output the binary form of an input number.

---

**Difficulty**: Easy

## Example

Input: `19`
Output: `00000000000000000000000000010011`

## Implementation

```c
void printInteger(int num) {
  for (int i = 31; i >= 0; i--) {
    int bit = (num >> i) & 1;
    printf("%d", bit);
  }
}
```
