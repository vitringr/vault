---
context:
  - "[[Endgame (Chess Phase)]]"
---

# Philidor Position

Fundamental [[Endgame (Chess Phase)|Endgame]] system that forces a [[Draw (Chess)|Draw]] for the defending side.

Involves a King and Rook vs King, Rook and Pawn scenario.

---

```chesser
fen: 8/8/8/8/2kp4/6R1/7r/3K4 b - - 0 1
```

The attacker is up a pawn and is threatening to promote, but if the defender gets to the Philidor position, he can then force a [[Draw (Chess)|Draw]] if played correctly.

## System

The defender's goal is to force a draw by repetition.

### Third Rank

First, the defender needs to get his Rook to the third rank away from the pomotion rank.

```chesser
fen: 8/8/8/8/3pk3/R7/7r/3K4 w - - 3 3
```

This will prevent the enemy King from advancing to the third rank, which would otherwise threaten [[Checkmate]] or a pawn escort.

### Escapism

From this position, the attacker doesn't really have any moves that can progress the game.

**Check**: If checked by the Rook, the defender can just move the King back and forth, always aligned with the pawn file.

Otherwise, the defender's Rook can use turn-skipping moves on the third rank to stall the game and increase the draw by repetition counter.

### Pawn Advance

The attacker can finally decide to advance their pawn to the third rank.

The defender should then move the Rook to the final rank, opposite of the promotion rank, and check repeatedly until a draw is forced.

```chesser
fen: 1R6/8/8/8/4k3/3p4/7r/3K4 b - - 1 4
```

Any mistakes from the attacker, like giving away his Rook, or getting too far from the pawn to defend it will again force the draw.
