---
tags:
  - "original"
context:
  - "[[WebGL]]"
  - "[[WebGL2]]"
---

# WebGL Drawing Particles

Concepts about drawing particles with WebGL.

---

There are different methods of drawing particles.

## Compute-based

The idea is to generate some state data (positions, velocities, etc) and update it every frame.

The problem is that the state data needs to be updated on the [[GPU]] (consider millions of particles), but the GPU is stateless.

Passing raw data from the GPU to the [[CPU]] and back can be very expensive.

The general solution to this is keeping the state data in the GPU and calculating it there. Solutions include techniques like [[Compute Shader|Compute Shaders]], [[Transform Feedback]], and [[Double Buffering]].

## Time-based

The idea is to avoid mutating particle state data, instead computing initial values affected by time.

Requires some number that represents time, which is constantly being incremented.

Requires that the simulation is [[Determinism|deterministic]], otherwise it couldn't be calculated just from initial conditions alone. See [[Chaos Theory]].
