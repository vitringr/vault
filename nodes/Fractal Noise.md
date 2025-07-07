---
context:
  - "[[Noise (Procedural Generation)]]"
---

# Fractal Noise

Combines multiple layers of noise with different frequencies and amplitudes.

---

The result is a [[Recursion|self-similar]], more complex version of the original.

Multiple _octaves_ (layers) of noise are added together, each with higher _frequency_ (details) and lower _amplitude_ (influence).

## Intuition

```
total += noise(coordinates *  10) * 0.5         // Octave 1
total += noise(coordinates *  20) * 0.25        // Octave 2
total += noise(coordinates *  40) * 0.125       // Octave 3
total += noise(coordinates *  80) * 0.0625      // Octave 4
total += noise(coordinates * 160) * 0.03125     // Octave 5
total += noise(coordinates * 320) * 0.015625    // Octave 6
```

## Implementation

```glsl
float getFractalNoise(vec2 point, int octaves) {
  float total = 0.0;
  float frequency = 1.0;
  float amplitude = 1.0;
  float maxValue = 0.0;

  for(int i = 0; i < octaves; i++) {
    total += getNoise(point * frequency) * amplitude;
    maxValue += amplitude;
    amplitude *= 0.5;
    frequency *= 2.0;
  }

  return total / maxValue;
}
```
