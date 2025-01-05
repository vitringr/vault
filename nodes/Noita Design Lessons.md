---
context:
  - "[[Game Design]]"
  - "[[Noita]]"
---

# Noita Design Lessons

## Roguelike

Making the game a hardcore permadeath roguelike solved many design problems.

It makes the player **pay close attention** to the simulated world, noticing and embracing the details way more than he would have if there were less at stake.

It also avoids solving some design problems, such as retrieving your corpse items from a pool of lava for example.

## Physics

Advanced sand simulation, basically.

There are also rigid body physics. Pixel art goes through some process that eventually triangulates it.

## Performance

The game only simulates the physics around the screen.

The pixel simulations are divided into sections, which run in parallel. To avoid sections overlapping and stuff, they separate the calculations of different sections in a checkboard-like pattern.
