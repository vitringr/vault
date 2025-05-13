---
tags:
  - "original"
aliases:
  - "journal"
context:
---

# Building Sandfall

Journal about creating the Sandfall project.

---

Starting from zero.

## Inspiration

For inspiration, the main thing is my affinity and love of [[Creative Coding]] and everything involving [[Particle System|Particle Systems]] and simulations. It doesn't take much to spark my interest in related fields.

Then there's [[Noita]]. It's one of my favorite games of all time.

## Self-doubt

Writing this in hindsight, but for a long time I thought that building such a sophisticated system is beyond my capabilities.

Skill issue as well as confidence issue on my side.

## Confidence Through Study

Studying [[Computer Graphics]], [[General Purpose GPU]] usage, and [[WebGL]], makes me feel more and more confident I can tackle on such a problem. And it also feels like these may just be the right tools for the job.

I made a bunch of particle systems already, and with my newly gained knowledge they are extremely efficient. Feels like I have lightning in my hands.

## Research

Researching how falling sand simulations are built.

There's a ton of stuff out there.

To my surprise, it's not as magical and impossible as I imagined it to be. In fact, turns out that without realizing it, I'm already familiar with the concepts used for such simulations.

## Cellular Automata

This is it. [[Cellular Automaton|Cellular Automata]].

In the past, I was fascinated with cellular automata, and things like the [[Game of Life]] as a famous example. But I never really spent the time to dive deep.

Seems like now is the time.

## Confidence

It seems like I have most of the prerequisites for building such a simulation.

Just do it.

## Logic

You get a cell, you get the data of its neighbors, you update the cell as well as its neighbors. You can mark the updated cells so that they don't get updated another time in the same frame.

## WebGL Build

Trying to reuse some of the logic in building particle systems.

I've built a [[Lattice]] of cells, each with a binary state, utilizing [[Double Buffering]] to swap [[Texture|Textures]] containing the data for each cell.

## Difficulties of Parallel Computing

It's so much more difficult when I have to compute all the cells synchronously.

_[[Race Condition|Race conditions]], race conditions, race conditions..._

It's definitely not as straightforward as the 'normal' [[CPU]] way of just updating an array of cells.

## Cell Perspective

Every cell should update its state independently.

I cannot just update it using its neighbor, because everything needs to happen simultaneously.

The cell itself has to get its surrounding and determine what it should be on the next frame.

## Three Too Many

For a 1:1 relationship, the cell perspective logic works perfectly.

However, adding a 3rd cell to the equation sometimes fucks it up.

**Duplication**: When two cells both want to become the third.

**Dissapearing**: When two cells both dissapear due to 'falling' on the third.

And probably many more problems.

## Recursive Neighbor Scan

An idea to avoid the abovemeantioned problems is to get the cell, the targeted neighbor for any interaction logic, and then get the neighbor's neighbors.

Without even trying it I feel like this will become an extreme bottleneck due to its recursive nature. Also I'm not even sure that it will fix all of the problems it's supposed to fix.

## Claiming System

What if we add more update loops and more data maps?

On the first iteration the cell 'claims' another cell, basically requesting interaction with it.

On the next iteration the claim requests are resolved, using some logic to pick the best requests.

## Swap Problem

Even if the 'Empty' : 'Sand' interaction is working as intended, there is also the problem of 'Water' and liquids in general, as well as gasses.

The problem is that the sand can swap with an empty cell, but it can also swap with water, as if it's sinking. Water can also swap with empty cells and possibly materials that will be lighter than sand.

Did anyone say [[Race Condition|Race Conditions]]?

## Density and Sorting

My friend Svetoslav came up with the idea of 'Density'.

Basically each type of cell can have a density level. For example:

1. Gasses
2. Liquids
3. Solids

Density is like an abstraction covering the same interactions of different elements.

He also said that by adding the concept of density, the problem can then be viewed as a 2D sorting problem.

## Layering

What if we split the interactions into diferent updates groups? Something like:

1. Empty : Gasses
2. Empty : Liquids
3. Empty : Solids
4. Gasses : Gasses
5. Liquids : Liquids
6. Solids : Solids
7. Gasses : Liquids
8. Liquids : Solids

This avoids many of the race conditions. It also makes the interaction logic much simpler, as it cuts some of the conditional logic otherwise needed.

The obvious drawback in terms of performance is that there are more update cycles. But I'm not even sure how bad it is, as on the other hand without the additional update groups, there will be way more conditional logic, which itself also affects performance.

## Perfection

I want the system to be perfect!

Most falling sand solutions that I've seen include imperfections by design. Things like cell duplication, cell dissapearing, undeterministic order due to race conditions, etc. Most of the time this is irrelevant, as you wont notice a few missing or duplicated pixels out of a thousand.

But I'll know.

I prefer that all of the randomness and noise is added by me, the developer, on purpose. Not by bug-features that I don't have control over and I don't know how to avoid.

## Block Cellular Automata

This might be the solution. [[Block Cellular Automaton]].

---

---

---

## Exponential Permutations

Presets are perfect, especially for binary cell types, but what about multiple types?

The problem is that the amount of presets increases exponentially when I add more cell types:

- **2 types**: `2⁴ = 16` presets.
- **3 types**: `3⁴ = 81` presets.
- **4 types**: `4⁴ = 256` presets.
- **5 types**: `5⁴ = 625` presets.
- **6 types**: `6⁴ = 1296` presets.
- **7 types**: `7⁴ = 2401` presets.
- **8 types**: `8⁴ = 4096` presets.
- **9 types**: `9⁴ = 6561` presets.

And what if I want at least `20` different elements for my simulation? This is equal to `160000` permutations that I have to hard-code.

Damn it.

## Layering for Presets

I can use the layering approach again, this time with the presets.

This will allow me to go for pairs of interactions, instead of the whole thing, where each pair has only `16` permutations, since there are only two elements.

This might work.

Remaining problem is that I'll still have to hard-code increasingly more presets for every new element added, since it needs to be able to interact with every other existing element, which again increases permutations exponentially.

But it's not that bad I think. It's still only `16` presets per pair, plus there's the advantage of having full arbitrary control over the interaction when creating presets.

## Multiple Element Blocks Problem

Turns out I can't easily combine layering with presets.

The problem comes from blocks that have 3 or more types of elements inside.

When calculating a layer of two types, it's not so simple to just skip or ignore the third type.

Imagine this scenario:

`E` = Empty
`W` = Water
`S` = Sand

Example of two different Empty:Water presets:

```
[W][E]  >  [E][E]
[E][W]  >  [W][W]

[W][W]  >  [E][W]
[E][W]  >  [W][W]
```

Notice how the top-right cell is different; first it's Empty, then it's Water, leading to different outputs.

This works perfectly, but what if the top-right cell for example is Sand?

```
[W][S]  >  [?][?]
[E][W]  >  [?][?]
```

Even if I only look at the Empty:Water presets, there are still two different outputs depending on the state of the top-right cell, which is undefined.

What do I do with the 'other' cell?

## Other Type Element Solution

What if I add another element type called _'other'_, and treat any elements that are not a part of the current layer's elemnt pair as _'other'_?

This way, I'll have a preset that can handle _other_ elements in a layer.

In the Empty:Water example above, this situation:

```
[W][S]  >  [?][?]
[E][W]  >  [?][?]
```

can be transpiled into this situation:

```
[W][O]  >  [E][O]
[E][W]  >  [W][W]
```

where `O` = _other_.

Even situations with 4 different elements can be transpiled down to:

```
[W][X]  >  [E][X]
[E][Y]  >  [W][Y]
```

Now I can hard-code presets which kind of 'skip' or 'freeze' any _other_ elements.

The obvious drawback is that instead of `16`, I would need to hard-code `81` permutations for every interaction.

**Skip Suggestion**: AI suggested that I can skip over blocks with more than two elements, avoiding these problems. This is somewhat of a solution, but I'm pretty sure it will lead to cases of unresolved (stuck) blocks that never get updated, or situations where the updates happen very slowly due to constant skips.

## Conditional Logic Blocks

What if I go back to conditional logic, but only for the blocks?

If they are 2x2 [[Margolus Neighborhood]] blocks, then it's feasible to do perfect conditional logic per individual block.

This will prevent many, if not all, problems such as duplication, vanishing, race conditions, etc.

## Hybrid Approach

What if I go for both block-level conditional logic combined with block presets?

If a block contains only two element types - use presets.
If it contains more than two element types - use conditional logic.

That might do it. But first I need to get the presets working.

## Encoding Presets

Since the presets target only two cell types, the cell types can be stored as bits.

With four cells (bits) per block, the patterns can be encoded as 4bit binary numbers, which is in the `[0. 15]` decimal range.

Function encoding the 4 block bits into an integer:

```GLSL
int encodePattern(ivec4 blockBits) {
  return blockBits.r +       // R: bottom-left cell
         blockBits.g * 2 +   // G: bottom-right cell
         blockBits.b * 4 +   // B: top-left cell
         blockBits.a * 8;    // A: top-right cell
}
```

And a function decoding them back into bits:

```GLSL
ivec4 decodePattern(int pattern) {
  return ivec4(
     pattern       & 1,   // R: bottom-left cell
    (pattern >> 1) & 1,   // G: bottom-right cell
    (pattern >> 2) & 1,   // B: top-left cell
    (pattern >> 3) & 1    // A: top-right cell
  );
}
```

The beauty of this is that choosing the next pattern becomes extremely computationally efficient.

All of the pair interaction patterns are just numbers in an `int[16]` array:

```GLSL
const int EMPTY_BLOCK[16] = int[16](0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15);
const int EMPTY_SAND[16]  = int[16](0,  1,  2,  3,  1,  3,  3,  7,  2,  3,  3, 11,  3,  7, 11, 15);
const int EMPTY_WATER[16] = int[16](0,  2,  1,  3,  1,  3,  3, 11,  2,  3,  3,  7,  3,  7, 11, 15);
```

And it all comes down to accessing this array by index:

```GLSL
int oldPattern = encodePattern(blockElements);

int newPattern = EMPTY_SAND[oldPattern];
```

## Drawing Patterns Tool

Created a simple `pattern-draw.js` tool that fills in 2x2 blocks of binary cells and outputs the patterns array.

It works perfectly, and is also one of the worst pieces of code I've ever written.

## Input Patch

Added way more input options to the project.

Keyboard input feels good when spawning different elements.

## Multiple Pairs

First, It checks how many unique elements the block contains:

```GLSL
int countUniqueElements(ivec4 elements) {
  int uniqueCount = 1;

  bool e1 = elements[1] != elements[0];
  bool e2 = elements[2] != elements[0] && elements[2] != elements[1];
  bool e3 = elements[3] != elements[0] && elements[3] != elements[1] && elements[3] != elements[2];

  uniqueCount += int(e1) + int(e2) + int(e3);

  return uniqueCount;
}
```

Then, based on the result:

- **One**: Nothing changes. This could be different in the future.
- **Two**: Logic that gets the pair of elements and chooses the correct pattern for their interaction.
- **More**: Work in progress. Will probably be conditional logic.

## Optimization

To avoid conditional logic, all of the interaction patterns could be stored in a single array:

```GLSL
const int INTERACTIONS[10 * 16] = int[10 * 16](
  0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, // EMPTY - BLOCK
  0,  1,  2,  3,  1,  3,  3,  7,  2,  3,  3, 11,  3,  7, 11, 15, // EMPTY - SAND
  0,  2,  1,  3,  1,  3,  3, 11,  2,  3,  3,  7,  3,  7, 11, 15, // EMPTY - WATER
  0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, // EMPTY - FIRE
  0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, // BLOCK - SAND
  0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, // BLOCK - WATER
  0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, // BLOCK - FIRE
  0,  4,  8, 12,  4, 12, 12, 13,  8, 12, 12, 14, 12, 13, 14, 15, // SAND - WATER
  0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, // SAND  - FIRE
  0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15  // WATER - FIRE
);
```

And be accessed by the pair of element types (in ascending order) through a function that only God understands at this point:

```GLSL
int getInteractionsIndex(ivec2 pair) {
  return 16 * (ELEMENTS_COUNT * pair.x - (pair.x * (pair.x + 1)) / 2 + (pair.y - pair.x - 1));
}
```

Also created functions that map `ivec4` integer vectors containing two unique values into bit values in the `[0, 1]` integer range and back. The idea of this is that different cell elements can be various integers, but to use them with the patterns they have to behave as `[0, 1]` bits.

> [!Note] Hindsight
>
> Don't waste time optimizing things before they are completed...
>
> Might turn out they won't be used...
>
> _Sigh,_ Anyways.

## Ehh

Might turn out that everything will be conditional logic.
