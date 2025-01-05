---
aliases:
  - Partitioning Cellular Automaton
context:
  - "[[Cellular Automaton]]"
---

# Block Cellular Automaton

[[Cellular Automaton]] in which the lattice of cells is divided into non-overlapping blocks with state updates based on those blocks.

---

**Partitioning**: The lattice of cells is divided into fixed, non-overlapping blocks of equal size.

See [[Margolus Neighborhood]]

**Blocks**: Each block is treated as a single unit for rule application.

**Alternation**: Alternates between block partition schemes.

**Evolution**: State updates can be applied simultaneously and synchronously to all blocks in the partition. Then, the partition is shifted and the same operation is repeated in the next time step, and so forth.

**Reversibility**: Easier to design reversible block cellular automata.

## Uses

**Compared to Conventional CA**: Block CA don't introduce any additional power compared to conventional CA, meaning that any block CA behavior can be simulated on a conventional CA.

**Parallel Computing**: Block CA can be very efficient for parallel computing and the use of [[GPU|GPU's]] because of how blocks can be updated simultaneously and synchronously.
