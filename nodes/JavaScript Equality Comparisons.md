---
context:
  - "[[JavaScript]]"
---

# JavaScript Equality Comparisons

Determining equality between JavaScript entities.

---

**Loose Equality (`==`)**: Compares value after performing automatic [[Type Conversion]] if types differ.

**Strict Equality (`===`)**: Compares both value and type without performing [[Type Conversion]].

> [!Tip] Best Practice
> Always use the `===` strict equality comparison.

**`Object.is`**: The `Object.is()` static method determines whether two values are the same value.
