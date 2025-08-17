---
context:
  - "[[Computer Memory]]"
  - "[[Computer Science]]"
---

# Memory Management

The systematic control of [[Computer Memory]] allocation and utilization.

---

Memory management involves:

- **Allocation**: Assigning memory to processes when they request it.
- **Deallocation**: Freeing memory when a process terminates or no longer needs it.
- **Protection**: Prevents processes from accessing memory they do not own.
- **Optimization**: Minimazing fragmentation and maximizing utilization.

## Fragmentation

Wasted memory space due to inefficient allocation.

Occurs when there are gaps of unused memory between used memory blocks. The gaps may not always be large enough to be used for additional allocation.

## Requesting Memory

Programs can request memory from the [[Operating System]].

If there is enough memory available, the operating system allocates a chunk of memory for the program to use.

Programs can later request additional memory if needed.

**Performance Impact**: Memory requests are expensive and can degrade performance.
