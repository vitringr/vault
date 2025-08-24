---
context:
  - "[[Computer Memory]]"
  - "[[Computer Science]]"
---

# Memory Layout

The memory segments of a [[Computer Program]].

---

Computer program memory can be largely categorized into two sections: read-only and read/write.

Typical layout of memory segments:

1. Code Segment
2. Static Data Segment
3. Heap Segment
4. Stack Segment

```
┌────────────┐
│    Stack   │ ← Grows downward
├────────────┤
│    Heap    │ ← Grows upward
├────────────┤
│     BSS    │ (Uninitialized data)
├────────────┤
│    Data    │ (Initialized globals)
├────────────┤
│    Code    │ (Read-only)
└────────────┘
```

| Segment   | Managed By | Lifetime         | Access Speed |
| --------- | ---------- | ---------------- | ------------ |
| **Code**  | Compiler   | Program duration | Fast         |
| **Data**  | Compiler   | Program duration | Fast         |
| **Heap**  | Programmer | Manual (`free`)  | Slow         |
| **Stack** | CPU        | Function-scoped  | Very Fast    |

## Code

(aka. Text Segment)

Contains executable [[Machine Code]].

Is generally read-only and fixed size.

## Static Data

(aka. Global/Static Segment)

Contains static data.

**Data**: Contains initialized static data.

**BSS**: Contains uninitialized static data.

## Heap

Contains dynamically allocated memory.

Can expand in size.

Fragmentation can occur over time.

## Stack

See [[Call Stack]]
