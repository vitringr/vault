---
aliases:
context:
  - "[[Endgame (Chess Phase)]]"
---

# Queen vs Seventh Rank Pawn

Fundamental [[Endgame (Chess Phase)|Endgame]] system that forces a win for the attacking side.

Involves a King and Queen vs King and Pawn on the seventh rank.

---

```chesser
fen: Q7/1K6/8/8/8/4k3/3p4/8 w - - 0 1
```

The defender threatens to promote the pawn and [[Draw (Chess)|Draw]] the game, but the attacker can force a [[Checkmate]] if he plays the system properly.

**After Pawn Race**: The position can often arise after pawn race scenarios, where one side is always first with the Queen promotion.

## System

The idea is to check the enemy King repeatedly while getting closer with the Queen, and then with the King.

When close enough with both King and Queen, the enemy pawn can be removed, leading to a [[King and Queen Checkmate]].

### Queen Zig Zag

First, get close with the Queen by constantly checking the enemy King or pawn.

The enemy King has to remain close to the pawn, otherwise it would be captured for free.

### Table Chase

When the Queen is next to the enemy pawn and King, there are only a few adequate positions that the three pieces can be in.

The goal of the Queen is to prevent promotion by either:

- Checking the enemy King
- [[Pin (Chess Tactic)|Pinning]] the pawn to him.

### King Move

Every few moves, the enemy King will be forced to hide behind the pawn, occupying its promotion rank.

This move allows the attacker to get one step closer with the King.

```chesser
fen: 8/1K6/8/8/8/4Q3/3p4/3k4 w - - 14 8
```

Repeat this until the King is close enough.

### Finish

When the King is close enough, the pawn can be captured.

```chesser
fen: 8/8/8/8/8/2QK4/3p4/3k4 b - - 55 28
```

Sometimes the Queen will be able to safely occupy the promotion square, which also results in an easy forced win:

```chesser
fen: 8/8/2K5/8/8/2k5/3p4/3Q4 b - - 19 10
```

When the pawn is captured, finish the game with a simple [[King and Queen Checkmate]].
