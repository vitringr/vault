---
context:
  - "[[A-Star Algorithm]]"
---

# Weighted A-Star Algorithm

Variation of the [[A-Star Algorithm]] that uses scalar weights in order to bias its heuristic function.

---

See [[A-Star Algorithm#Bounded Relaxation]].

Biasing the heuristic function can speed up the search process at the expense of admissibility.

`F(n) = X * G(n) + H(n)`, where `X` is an arbitrary weight value.
If `X > 1`, the algorithm becomes biased towards nodes that are closer to the goal.
