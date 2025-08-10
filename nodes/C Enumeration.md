---
context:
  - "[[C (Programming Language)]]"
  - "[[Enumeration]]"
---

# C Enumeration

User-defined data that assigns names to integer constants.

---

Enums help to make code more readable and maintainable.

Default values start at `0` and increment by `1`.

```c
enum Color { RED, GREEN, BLUE };
enum Color a = RED;
```

```c
enum Weekday {
  MONDAY,    // 0
  TUESDAY,   // 1
  WEDNESDAY, // 2
  THURSDAY,  // 3
  FRIDAY,    // 4
  SATURDAY,  // 5
  SUNDAY     // 6
};
```
