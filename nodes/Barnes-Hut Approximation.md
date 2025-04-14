---
context:
  - "[[Simulation]]"
  - "[[Particle System]]"
---

# Barnes-Hut Approximation

Method of approximating the [[N-body Problem]] using [[Quadtree]] subdivision.

---

Given a field of objects, the naive approach is to directly calculate interactions between every pair of objects. However, this becomes computationally infeasible as the number of objects grows, since the complexity scales as `O(n²)`.

The core idea behind the Barnes-Hut approximation is to organize the objects (represented as coordinate points) into a [[Quadtree]] - a hierarchical spatial structure with recursive subdivisions.

- Nearby objects are treated individually, ensuring high accuracy for close-range interactions.
- Distant objects are approximated as a single combined center of mass, reducing computational overhead.

The combined center of mass for each quadtree subdivision is computed as the weighted average of all objects within that region.

This approximation reduces the time complexity to `O(n log n)`.
