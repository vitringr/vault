---
aliases:
  - Cellular Automata
context:
  - "[[Automata Theory]]"
  - "[[Concurrent Model of Computation]]"
---

# Cellular Automaton

Discrete [[Concurrent Model of Computation]] consisting of a [[Lattice]] of cells, each in one of a finite number of states. The state of each cell evolves over discrete time steps according to a set of rules based on the states of neighboring cells.

---

**Cell States**: Each cell is in one of a finite number of states.

**Cell Neighbors**: Each cell has a set of neighboring cells.

**Evolution**: Each discrete time step evolves the state of cells using predefined rules based on the cell's neighbors.

**Dimensions**: The grid can be in any finite number of dimensions.

**Boundary**: The grid can have edges, it can be periodic (wrapping), or it can be infinite.

**Classification**:

1. **Class 1**: Converges to a uniform state.
2. **Class 2**: Forms periodic or stable structures.
3. **Class 3**: Produces chaotic, random-like behavior.
4. **Class 4**: Forms complex and interesting structures.

**Reversibility**:
A cellular automaton is _reversible_ if for every configuration there is exactly one past configuration (called _preimage_). This can be seen as a [[Bijection]] of state configurations.

For reversible cellular automata, configurations without preimages are called [[Garden of Eden (Cellular Automaton)]].
