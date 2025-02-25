---
context:
  - "[[Checkmate Pattern]]"
---

# Two Bishops Checkmate

Rare but fundamental [[Checkmate Pattern]] done by a King and two Bishops.

---

From any King & two Bishops vs King position, the idea is to push the enemy King into a corner of the board and deliver a systematic [[Checkmate|checkmate]].

**Forced**: Checkmate can always be forced in this scenario.

**Full System**: From any position, the system is this:

1. Form a center cone.
2. Push the King.
3. Checkmate.

## Center Cone

The goal is get the Bishops together in the center so that they form a 'cone', essentially trapping the enemy King in less than a quarter of the board.

```chesser
fen: 8/8/3k4/8/3BB3/8/4K3/8 w - - 0 1
```

## Push the King

Use the King to push with [[Opposition (Chess)|Opposition]] from the side.

Once there is enough space, use the Bishops to close the cone one step deeper. Generally start with the Bishop that is further away from your King.

```chesser
fen: 8/3k4/8/2B2K2/4B3/8/8/8 b - - 0 1
```

**Together**: Bring the Bishops back together. There should be only one move that separates them, and then they should align together again.

**Final Rank**: Keep repeating the push until the enemy King is on the final rank.

```chesser
fen: 1k6/8/1BBK4/8/8/8/8/8 b - - 0 1
```

## Checkmate

When the King is on the back rank, use one of two patterns to deliver checkmate without causing an accidental [[Stalemate (Chess)]].

### Corner

Move your King into the edge of the board, aligned with the Bishops:

```chesser
fen: 1k6/8/KBB5/8/8/8/8/8 b - - 0 1
```

**From 3 to 2**: The enemy King can move between 3 squares. The goal is to block the 3rd square, leaving him with only 2 left:

```chesser
fen: 1k6/3B4/KB6/8/8/8/8/8 b - - 0 1
```

**Finish**: Skip a turn with the Bishop and, finally, check the King on the second square, and checkmate him on the final square.

```chesser
fen: 1k6/3B4/K7/2B5/8/8/8/8 w - - 0 1
```
