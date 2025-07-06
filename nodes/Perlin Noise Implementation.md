---
tags:
  - "code"
  - "original"
context:
  - "[[Perlin Noise]]"
---

# Perlin Noise Implementation

Implementation of [[Perlin Noise]] with [[Fractal Noise]] in different languages.

## GLSL

Implementation in [[GLSL]]:

```glsl
const vec2 GRADIENTS[32] = vec2[32](
  vec2( 1.0,                 0.0),
  vec2( 0.9807852804032304,  0.1950903220161282),
  vec2( 0.9238795325112867,  0.3826834323650898),
  vec2( 0.8314696123025452,  0.5555702330196022),
  vec2( 0.7071067811865476,  0.7071067811865475),
  vec2( 0.5555702330196023,  0.8314696123025452),
  vec2( 0.3826834323650898,  0.9238795325112867),
  vec2( 0.1950903220161283,  0.9807852804032304),
  vec2( 0.0,                 1.0               ),
  vec2(-0.1950903220161282,  0.9807852804032304),
  vec2(-0.3826834323650897,  0.9238795325112867),
  vec2(-0.5555702330196022,  0.8314696123025453),
  vec2(-0.7071067811865475,  0.7071067811865476),
  vec2(-0.8314696123025453,  0.5555702330196022),
  vec2(-0.9238795325112867,  0.3826834323650899),
  vec2(-0.9807852804032304,  0.1950903220161286),
  vec2(-1.0,                 0.0               ),
  vec2(-0.9807852804032304, -0.1950903220161283),
  vec2(-0.9238795325112868, -0.3826834323650896),
  vec2(-0.8314696123025455, -0.5555702330196020),
  vec2(-0.7071067811865477, -0.7071067811865475),
  vec2(-0.5555702330196022, -0.8314696123025452),
  vec2(-0.3826834323650903, -0.9238795325112865),
  vec2(-0.1950903220161286, -0.9807852804032303),
  vec2( 0.0,                -1.0               ),
  vec2( 0.1950903220161283, -0.9807852804032304),
  vec2( 0.3826834323650897, -0.9238795325112866),
  vec2( 0.5555702330196018, -0.8314696123025455),
  vec2( 0.7071067811865474, -0.7071067811865477),
  vec2( 0.8314696123025452, -0.5555702330196022),
  vec2( 0.9238795325112865, -0.3826834323650904),
  vec2( 0.9807852804032303, -0.1950903220161287)
);

float getRandom(vec2 v) {
  return fract(sin(dot(v, vec2(12.9898, 78.233))) * 43758.5453);
}

vec2 getRandomGradient(vec2 coordinates) {
  float randomValue = getRandom(coordinates);
  int index = int(randomValue * 32.0) & 31;
  return GRADIENTS[index];
}

vec2 fade(vec2 t) {
    return t * t * t * (t * (t * 6.0 - 15.0) + 10.0);
}

float getNoise(vec2 point) {
  vec2 gridIndex    = floor(point);
  vec2 gridFraction = fract(point);

  vec2 gradient_BL = getRandomGradient(gridIndex);
  vec2 gradient_BR = getRandomGradient(gridIndex + vec2(1.0, 0.0));
  vec2 gradient_TL = getRandomGradient(gridIndex + vec2(0.0, 1.0));
  vec2 gradient_TR = getRandomGradient(gridIndex + vec2(1.0, 1.0));

  vec2 to_BL = gridFraction;
  vec2 to_BR = gridFraction - vec2(1.0, 0.0);
  vec2 to_TL = gridFraction - vec2(0.0, 1.0);
  vec2 to_TR = gridFraction - vec2(1.0, 1.0);

  float dot_BL = dot(to_BL, gradient_BL);
  float dot_BR = dot(to_BR, gradient_BR);
  float dot_TL = dot(to_TL, gradient_TL);
  float dot_TR = dot(to_TR, gradient_TR);

  gridFraction = fade(gridFraction);

  float bot = mix(dot_BL, dot_BR, gridFraction.x);
  float top = mix(dot_TL, dot_TR, gridFraction.x);

  float perlinNoise = mix(bot, top, gridFraction.y);

  return perlinNoise * 0.70710678 + 0.5;
}

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

## TypeScript

Implementation in [[TypeScript]]:

```typescript
const PERMUTATIONS = new Uint8Array([
  9, 159, 97, 66, 201, 20, 105, 192, 168, 220, 72, 253, 5, 88, 190, 162, 163,
  61, 129, 217, 4, 194, 255, 204, 115, 185, 59, 33, 48, 177, 200, 117, 113, 248,
  7, 95, 133, 121, 1, 176, 144, 8, 127, 39, 62, 193, 236, 81, 244, 112, 75, 51,
  80, 11, 70, 0, 175, 60, 116, 142, 102, 135, 85, 137, 106, 32, 13, 91, 101,
  232, 47, 170, 229, 71, 131, 86, 42, 76, 100, 187, 145, 240, 182, 19, 53, 108,
  15, 87, 73, 235, 130, 136, 216, 41, 28, 74, 155, 68, 225, 183, 38, 231, 156,
  211, 64, 228, 152, 254, 46, 154, 207, 212, 17, 83, 150, 203, 109, 50, 195, 34,
  251, 55, 45, 215, 184, 96, 16, 179, 43, 208, 148, 245, 138, 132, 37, 164, 189,
  118, 181, 30, 171, 18, 226, 146, 230, 107, 63, 78, 134, 196, 44, 198, 3, 93,
  25, 123, 158, 219, 69, 124, 247, 140, 103, 94, 188, 57, 160, 213, 98, 89, 218,
  153, 90, 147, 6, 56, 92, 122, 49, 29, 214, 243, 111, 139, 99, 238, 173, 104,
  197, 202, 51, 250, 205, 141, 119, 166, 21, 58, 234, 165, 239, 77, 172, 36, 2,
  237, 167, 110, 241, 126, 210, 24, 209, 233, 149, 14, 224, 114, 18, 227, 186,
  242, 174, 67, 161, 65, 31, 222, 40, 10, 206, 143, 27, 221, 22, 120, 178, 246,
  52, 169, 249, 82, 35, 84, 79, 125, 54, 23, 128, 199, 252, 157, 223, 26, 191,
  12,
  // Duplicate
  9, 159, 97, 66, 201, 20, 105, 192, 168, 220, 72, 253, 5, 88, 190, 162, 163,
  61, 129, 217, 4, 194, 255, 204, 115, 185, 59, 33, 48, 177, 200, 117, 113, 248,
  7, 95, 133, 121, 1, 176, 144, 8, 127, 39, 62, 193, 236, 81, 244, 112, 75, 51,
  80, 11, 70, 0, 175, 60, 116, 142, 102, 135, 85, 137, 106, 32, 13, 91, 101,
  232, 47, 170, 229, 71, 131, 86, 42, 76, 100, 187, 145, 240, 182, 19, 53, 108,
  15, 87, 73, 235, 130, 136, 216, 41, 28, 74, 155, 68, 225, 183, 38, 231, 156,
  211, 64, 228, 152, 254, 46, 154, 207, 212, 17, 83, 150, 203, 109, 50, 195, 34,
  251, 55, 45, 215, 184, 96, 16, 179, 43, 208, 148, 245, 138, 132, 37, 164, 189,
  118, 181, 30, 171, 18, 226, 146, 230, 107, 63, 78, 134, 196, 44, 198, 3, 93,
  25, 123, 158, 219, 69, 124, 247, 140, 103, 94, 188, 57, 160, 213, 98, 89, 218,
  153, 90, 147, 6, 56, 92, 122, 49, 29, 214, 243, 111, 139, 99, 238, 173, 104,
  197, 202, 51, 250, 205, 141, 119, 166, 21, 58, 234, 165, 239, 77, 172, 36, 2,
  237, 167, 110, 241, 126, 210, 24, 209, 233, 149, 14, 224, 114, 18, 227, 186,
  242, 174, 67, 161, 65, 31, 222, 40, 10, 206, 143, 27, 221, 22, 120, 178, 246,
  52, 169, 249, 82, 35, 84, 79, 125, 54, 23, 128, 199, 252, 157, 223, 26, 191,
  12,
]) as Readonly<Uint8Array>;

const GRADIENTS_X = new Float32Array([
  1.0, 0.9807852804032304, 0.9238795325112867, 0.8314696123025452,
  0.7071067811865476, 0.5555702330196023, 0.38268343236508984,
  0.19509032201612833, 0.0, -0.1950903220161282, -0.3826834323650897,
  -0.555570233019602, -0.7071067811865475, -0.8314696123025453,
  -0.9238795325112867, -0.9807852804032304, -1.0, -0.9807852804032304,
  -0.9238795325112868, -0.8314696123025455, -0.7071067811865477,
  -0.5555702330196022, -0.38268343236509034, -0.19509032201612866, 0.0,
  0.1950903220161283, 0.38268343236509, 0.5555702330196018, 0.7071067811865474,
  0.8314696123025452, 0.9238795325112865, 0.9807852804032303,
]) as Readonly<Float32Array>;

const GRADIENTS_Y = new Float32Array([
  0.0, 0.19509032201612825, 0.3826834323650898, 0.5555702330196022,
  0.7071067811865475, 0.8314696123025452, 0.9238795325112867,
  0.9807852804032304, 1.0, 0.9807852804032304, 0.9238795325112867,
  0.8314696123025453, 0.7071067811865476, 0.5555702330196022,
  0.3826834323650899, 0.1950903220161286, 0.0, -0.19509032201612836,
  -0.38268343236508967, -0.555570233019602, -0.7071067811865475,
  -0.8314696123025452, -0.9238795325112865, -0.9807852804032303, -1.0,
  -0.9807852804032304, -0.9238795325112866, -0.8314696123025455,
  -0.7071067811865477, -0.5555702330196022, -0.3826834323650904,
  -0.19509032201612872,
]) as Readonly<Float32Array>;

function fade(t: number): number {
  return t * t * t * (t * (t * 6 - 15) + 10);
}

function lerp(a: number, b: number, step: number): number {
  return a + step * (b - a);
}

export function get(x: number, y: number): number {
  const xIndex = Math.floor(x) & 255;
  const yIndex = Math.floor(y) & 255;

  const xFraction = x - Math.floor(x);
  const yFraction = y - Math.floor(y);

  const xFade = fade(xFraction);
  const yFade = fade(yFraction);

  const gradient_BL = PERMUTATIONS[PERMUTATIONS[xIndex] + yIndex] & 31;
  const gradient_BR = PERMUTATIONS[PERMUTATIONS[xIndex + 1] + yIndex] & 31;
  const gradient_TL = PERMUTATIONS[PERMUTATIONS[xIndex] + yIndex + 1] & 31;
  const gradient_TR = PERMUTATIONS[PERMUTATIONS[xIndex + 1] + yIndex + 1] & 31;

  const dot_BL = GRADIENTS_X[gradient_BL] * xFraction + GRADIENTS_Y[gradient_BL] * yFraction;
  const dot_BR = GRADIENTS_X[gradient_BR] * (xFraction - 1) + GRADIENTS_Y[gradient_BR] * yFraction;
  const dot_TL = GRADIENTS_X[gradient_TL] * xFraction + GRADIENTS_Y[gradient_TL] * (yFraction - 1);
  const dot_TR = GRADIENTS_X[gradient_TR] * (xFraction - 1) + GRADIENTS_Y[gradient_TR] * (yFraction - 1);

  const bot = lerp(dot_BL, dot_BR, xFade);
  const top = lerp(dot_TL, dot_TR, xFade);

  return lerp(bot, top, yFade) * 0.70710678118654 + 0.5;
}

export function getFractal(x: number, y: number, octaves: number): number {
  let total = 0.0;
  let frequency = 1.0;
  let amplitude = 1.0;
  let maxValue = 0.0;

  for (let i = 0; i < octaves; i++) {
    total += get(x * frequency, y * frequency) * amplitude;
    maxValue += amplitude;
    amplitude *= 0.5;
    frequency *= 2.0;
  }

  return total / maxValue;
}
```
