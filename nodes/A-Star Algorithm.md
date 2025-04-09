---
aliases:
  - A-Star Pathfinding
  - A-Star Search Algorithm
context:
  - "[[Pathfinding]]"
  - "[[Algorithm]]"
---

# A-Star Algorithm

(A\* Algorithm)

Versatile pathfinding and graph traversal algorithm.

---

Given a [[Weighted Graph]], a source node and a goal node, the algorithm can find the shortest path (with respect to the given weights) from the source to the goal.

**Complete**: On finite graphs with non-negative edge weights, A\* is guaranteed to terminate and to find a path if one exists.

**Admissible**: Can guarantee to return an optimal solution. If the heuristic is admissible, then A\* is admissible.

## Heuristics

The algorithm uses [[Heuristic]] functions to guide its search.

A\* selects the path that minimizes:
`F(n) = G(n) + H(n)`
Where `n` is the next node on the path, `G(n)` is the cost of the path from the start node to `n`, and `H(n)` is the estimate of the cheapest path, or distance, from `n` to the goal.

## Bounded Relaxation

While the admissability of A\* can guarantee an optimal solution, it also means that it might have to examine a lot of nodes.

It is possible to 'relax' the admissibility, speeding up the search process at the expense of optimality.

The heuristic function can be modified by [[Scalar]] weights.

See [[Weighted A-Star Algorithm]].

## Pseudocode

```
iterate() {
    if open is empty:
        terminate; // No path found

    current = best cell from open; // Lowest F value

    if current === target:
        terminate; // Path found

    remove current from open;
    add current to closed;

    for each of current.neighbors:
        if neighbor is block or neighbor is in closed:
            continue;

        totalG = current.G + cost to move to neighbor

        if neighbor is not in open:
            add neighbor to open;
            neighbor.parent = current;
            neighbor.G = totalG;
            neighbor.H = heuristic(neighbor, target);
            neighbor.F = neighbor.G + neighbor.H;
        else if totalG < neighbor.G:
                neighbor.parent = current;
                neighbor.G = totalG;
                neighbor.F = neighbor.G + neighbor.H; // Update F because G has changed
```
