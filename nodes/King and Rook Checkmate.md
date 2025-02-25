---
context:
  - "[[Checkmate Pattern]]"
---

# King and Rook Checkmate

Fundamental [[Checkmate Pattern]] done by a King and Rook.

---

From any King & Rook vs King position, the basic idea is to box the enemy King into an edge of the board, and then deliver checkmate with the King and Rook together.

**Forced**: Checkmate can always be forced in this scenario.

```chesser
fen: 8/8/8/8/8/4K3/8/R3k3 w - - 0 1
```

## Kings Align

To checkmate a running King on the final file, have your King on an adjacent rank:

```chesser
fen: 5k2/R7/4K3/8/8/8/8/8 b - - 0 1
```

When the enemy King moves, follow him. If they're not positioned properly, move your Rook to skip one turn.

The goal is to align the Kings on the same rank:

```chesser
fen: 5k2/1R6/5K2/8/8/8/8/8 w - - 0 1
```

With the Kings aligned, deliver checkmate with the Rook.
