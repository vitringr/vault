---
context:
  - "[[Computer Memory]]"
  - "[[Computer Science]]"
---

#wip

# Memory Management

---

Memory management involves:

- **Allocation**: Assigning memory to processes when they request it.
- **Deallocation**: Freeing memory when a process terminates or no longer needs it.
- **Protection**: Prevents processes from accessing memory they do not own.
- **Optimization**: Minimazing fragmentation and maximizing utilization.

#wip
The [[Call Stack]] and [[Heap (Memory Management)|Heap]] reside in [[RAM]].

## Fragmentation

Wasted memory space due to inefficient allocation.

Occurs when there are gaps of unused memory between used memory blocks.

The gaps may not always be large enough to be used for additional allocation.

## Requesting Memory

Programs request memory allocation from the [[Operating System]].

If there is enough memory available, the operating system allocates a chunk of memory for the program to use.

Programs can later request additional memory if needed.

Requesting additional memory affect performance.
