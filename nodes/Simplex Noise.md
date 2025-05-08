---
aliases:
context:
---

#wip

# Simplex Noise

ad

---

## Attempt

INPUT IS IN SKEWED SPACE?

[Clarity](https://chat.deepseek.com/a/chat/s/cbe57c81-d606-4c11-a924-24dd9d930bae)

> **Me:**
> So, you're saying that the input (the user-provided xy vector) is actually in simplex space? And I use that simplex space input to convert it to square space for some calculations, and then go back to simplex again for the gradients and final output?

> **AI:**
> Yes, exactly! Here’s a clearer breakdown of the coordinate spaces and transformations in 2D simplex noise:
> 
> 1. Input is in Simplex Space (Cartesian Coordinates)
> The user provides (x, y) in standard Cartesian space, which we’ll call "simplex space" (where the noise is defined on a grid of equilateral triangles).
> 
> However, working directly with equilateral triangles is messy for calculations, so we temporarily transform the point into a sheared square grid ("square space") where each square is split into two right triangles (simplifying gradient selection and interpolation).
