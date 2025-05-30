---
tags:
  - "code"
  - "original"
context:
  - "[[Simplex Noise]]"
---

# Simplex Noise Implementation

[[Simplex Noise]] implementation in [[TypeScript]].

---

#wip

```typescript
import { Canvas2D } from "@utilities/canvas2d";
import { Vector2 } from "@utilities/vector";
import { Colors } from "@utilities/colors";

import { createNoise2D } from "./ref";

const F = 0.3660254037844386; // Skew factor
const G = 0.2113248654051871; // Unskew factor

const PERMUTATIONS = [
  // The permutations table is duplicated once so that it does not
  // overflow, even if the index exceeds 256. Otherwise % operations
  // would be needed to wrap it around.
  // PERFORMANCE: Optimize array structure.
  51, 160, 137, 91, 90, 15, 131, 13, 201, 95, 96, 53, 194, 233, 7, 225, 140, 36,
  103, 30, 69, 142, 8, 99, 37, 240, 21, 10, 23, 190, 6, 148, 247, 120, 234, 75,
  0, 26, 197, 62, 94, 252, 219, 203, 117, 35, 11, 32, 57, 177, 33, 88, 237, 149,
  56, 87, 174, 20, 125, 136, 171, 168, 68, 175, 74, 165, 71, 134, 139, 48, 27,
  166, 77, 146, 158, 231, 83, 111, 229, 122, 60, 211, 133, 230, 220, 105, 92,
  41, 55, 46, 245, 40, 244, 102, 143, 54, 65, 25, 63, 161, 1, 216, 80, 73, 209,
  76, 132, 187, 208, 89, 18, 169, 200, 196, 135, 130, 116, 188, 159, 86, 164,
  100, 109, 198, 173, 186, 3, 64, 52, 217, 226, 250, 124, 123, 5, 202, 38, 147,
  118, 126, 255, 82, 85, 212, 207, 206, 59, 227, 47, 16, 58, 17, 182, 189, 28,
  42, 223, 183, 170, 213, 119, 248, 152, 2, 44, 154, 163, 70, 221, 153, 101,
  155, 167, 43, 172, 9, 129, 22, 39, 253, 19, 98, 108, 110, 79, 113, 224, 232,
  178, 185, 112, 104, 218, 246, 97, 228, 251, 34, 242, 193, 238, 210, 144, 12,
  191, 179, 162, 241, 81, 51, 145, 235, 249, 14, 239, 107, 49, 192, 214, 31,
  181, 199, 106, 157, 184, 84, 204, 176, 115, 121, 50, 45, 127, 4, 150, 254,
  138, 236, 205, 93, 222, 114, 67, 29, 24, 72, 243, 141, 128, 195, 78, 66, 215,
  61, 156, 18,
  // Duplicate
  51, 160, 137, 91, 90, 15, 131, 13, 201, 95, 96, 53, 194, 233, 7, 225, 140, 36,
  103, 30, 69, 142, 8, 99, 37, 240, 21, 10, 23, 190, 6, 148, 247, 120, 234, 75,
  0, 26, 197, 62, 94, 252, 219, 203, 117, 35, 11, 32, 57, 177, 33, 88, 237, 149,
  56, 87, 174, 20, 125, 136, 171, 168, 68, 175, 74, 165, 71, 134, 139, 48, 27,
  166, 77, 146, 158, 231, 83, 111, 229, 122, 60, 211, 133, 230, 220, 105, 92,
  41, 55, 46, 245, 40, 244, 102, 143, 54, 65, 25, 63, 161, 1, 216, 80, 73, 209,
  76, 132, 187, 208, 89, 18, 169, 200, 196, 135, 130, 116, 188, 159, 86, 164,
  100, 109, 198, 173, 186, 3, 64, 52, 217, 226, 250, 124, 123, 5, 202, 38, 147,
  118, 126, 255, 82, 85, 212, 207, 206, 59, 227, 47, 16, 58, 17, 182, 189, 28,
  42, 223, 183, 170, 213, 119, 248, 152, 2, 44, 154, 163, 70, 221, 153, 101,
  155, 167, 43, 172, 9, 129, 22, 39, 253, 19, 98, 108, 110, 79, 113, 224, 232,
  178, 185, 112, 104, 218, 246, 97, 228, 251, 34, 242, 193, 238, 210, 144, 12,
  191, 179, 162, 241, 81, 51, 145, 235, 249, 14, 239, 107, 49, 192, 214, 31,
  181, 199, 106, 157, 184, 84, 204, 176, 115, 121, 50, 45, 127, 4, 150, 254,
  138, 236, 205, 93, 222, 114, 67, 29, 24, 72, 243, 141, 128, 195, 78, 66, 215,
  61, 156, 18,
] as const;

const GRADIENTS_32: Vector2[] = [
  new Vector2(1, 0),
  new Vector2(0.9807852804032304, 0.19509032201612825),
  new Vector2(0.9238795325112867, 0.3826834323650898),
  new Vector2(0.8314696123025452, 0.5555702330196022),
  new Vector2(0.7071067811865476, 0.7071067811865475),
  new Vector2(0.5555702330196023, 0.8314696123025452),
  new Vector2(0.38268343236508984, 0.9238795325112867),
  new Vector2(0.19509032201612833, 0.9807852804032304),
  new Vector2(0, 1),
  new Vector2(-0.1950903220161282, 0.9807852804032304),
  new Vector2(-0.3826834323650897, 0.9238795325112867),
  new Vector2(-0.555570233019602, 0.8314696123025453),
  new Vector2(-0.7071067811865475, 0.7071067811865476),
  new Vector2(-0.8314696123025453, 0.5555702330196022),
  new Vector2(-0.9238795325112867, 0.3826834323650899),
  new Vector2(-0.9807852804032304, 0.1950903220161286),
  new Vector2(-1, 0),
  new Vector2(-0.9807852804032304, -0.19509032201612836),
  new Vector2(-0.9238795325112868, -0.38268343236508967),
  new Vector2(-0.8314696123025455, -0.555570233019602),
  new Vector2(-0.7071067811865477, -0.7071067811865475),
  new Vector2(-0.5555702330196022, -0.8314696123025452),
  new Vector2(-0.38268343236509034, -0.9238795325112865),
  new Vector2(-0.19509032201612866, -0.9807852804032303),
  new Vector2(-1.8369701987210297e-16, -1),
  new Vector2(0.1950903220161283, -0.9807852804032304),
  new Vector2(0.38268343236509, -0.9238795325112866),
  new Vector2(0.5555702330196018, -0.8314696123025455),
  new Vector2(0.7071067811865474, -0.7071067811865477),
  new Vector2(0.8314696123025452, -0.5555702330196022),
  new Vector2(0.9238795325112865, -0.3826834323650904),
  new Vector2(0.9807852804032303, -0.19509032201612872),
] as const;

const GRADIENTS_16_I: Vector2[] = [
  new Vector2(1, 0),
  new Vector2(1, 0),
  new Vector2(1, 1),
  new Vector2(0, 1),
  new Vector2(0, 1),
  new Vector2(0, 1),
  new Vector2(-1, 1),
  new Vector2(-1, 0),
  new Vector2(-1, 0),
  new Vector2(-1, 0),
  new Vector2(-1, -1),
  new Vector2(0, -1),
  new Vector2(0, -1),
  new Vector2(0, -1),
  new Vector2(1, -1),
  new Vector2(1, 0),
] as const;

const GRADIENTS_16: Vector2[] = [
  new Vector2(1, 0),
  new Vector2(0.9238795325112867, 0.3826834323650898),
  new Vector2(0.7071067811865476, 0.7071067811865475),
  new Vector2(0.38268343236508984, 0.9238795325112867),
  new Vector2(0, 1),
  new Vector2(-0.3826834323650897, 0.9238795325112867),
  new Vector2(-0.7071067811865475, 0.7071067811865476),
  new Vector2(-0.9238795325112867, 0.3826834323650899),
  new Vector2(-1, 0),
  new Vector2(-0.9238795325112868, -0.38268343236508967),
  new Vector2(-0.7071067811865477, -0.7071067811865475),
  new Vector2(-0.38268343236509034, -0.9238795325112865),
  new Vector2(0, -1),
  new Vector2(0.38268343236509, -0.9238795325112866),
  new Vector2(0.7071067811865474, -0.7071067811865477),
  new Vector2(0.9238795325112865, -0.3826834323650904),
] as const;

const GRADIENTS_12 = [
  new Vector2(1, 0),
  new Vector2(0.8660254037844387, 0.5),
  new Vector2(0.5, 0.8660254037844386),
  new Vector2(0, 1),
  new Vector2(-0.5, 0.8660254037844387),
  new Vector2(-0.8660254037844385, 0.5),
  new Vector2(-1, 0),
  new Vector2(-0.8660254037844388, -0.5),
  new Vector2(-0.5, -0.8660254037844385),
  new Vector2(0, -1),
  new Vector2(0.5, -0.866025403784439),
  new Vector2(0.8660254037844384, -0.5),
] as const;

const GRADIENTS_8 = [
  new Vector2(0, 1),
  new Vector2(0.7071067811865476, 0.7071067811865476),
  new Vector2(1, 0),
  new Vector2(0.7071067811865476, -0.7071067811865476),
  new Vector2(0, -1),
  new Vector2(-0.7071067811865476, -0.7071067811865476),
  new Vector2(-1, 0),
  new Vector2(-0.7071067811865476, 0.7071067811865476),
] as const;

function hash(x: number, y: number): number {
  // The number 256 (2⁸) is perfect for bitwise wrapping and for hardware performance.
  // Lower ranges produce visible artifacts and bias.
  // Higher ranges don't really improve visual output, while damaging performance.
  const x_wrapped = x & 255;
  const y_wrapped = y & 255;

  // For the guide, do PERMUTATIONS[x_wrapped + y_wrapped] to show
  // the directional bias produced.
  return PERMUTATIONS[x_wrapped + PERMUTATIONS[y_wrapped]];
}

function noise(input_triangle_x: number, input_triangle_y: number): number {
  // --------------------------------
  // -- Skew input to square space --
  // --------------------------------

  const S = (input_triangle_x + input_triangle_y) * F;
  const input_square_x = input_triangle_x + S;
  const input_square_y = input_triangle_y + S;

  // ------------------------
  // -- Find square origin --
  // ------------------------

  const A_square_x = Math.floor(input_square_x);
  const A_square_y = Math.floor(input_square_y);

  // -----------------------------------------------------
  // -- Find cell fraction and determine which triangle --
  // -----------------------------------------------------

  const fraction_x = input_square_x - A_square_x;
  const fraction_y = input_square_y - A_square_y;
  const isBotTriangle = fraction_x > fraction_y;

  // --------------------------------
  // -- Find other square vertices --
  // --------------------------------

  const B_square_x = A_square_x + (isBotTriangle ? 1 : 0);
  const B_square_y = A_square_y + (isBotTriangle ? 0 : 1);

  const C_square_x = A_square_x + 1;
  const C_square_y = A_square_y + 1;

  // --------------------------------------------
  // -- Unskew square origin to triangle space --
  // --------------------------------------------

  const TA = (A_square_x + A_square_y) * G;
  const A_triangle_x = A_square_x - TA;
  const A_triangle_y = A_square_y - TA;

  const TB = (B_square_x + B_square_y) * G;
  const B_triangle_x = B_square_x - TB;
  const B_triangle_y = B_square_y - TB;

  const TC = (C_square_x + C_square_y) * G;
  const C_triangle_x = C_square_x - TC;
  const C_triangle_y = C_square_y - TC;

  // -------------------------------------------
  // -- Difference between input and vertices --
  // -------------------------------------------

  const delta_A_x = input_triangle_x - A_triangle_x;
  const delta_A_y = input_triangle_y - A_triangle_y;

  const delta_B_x = input_triangle_x - B_triangle_x;
  const delta_B_y = input_triangle_y - B_triangle_y;

  const delta_C_x = input_triangle_x - C_triangle_x;
  const delta_C_y = input_triangle_y - C_triangle_y;

  // -------------------------------------------------
  // -- Select gradients from square-space vertices --
  // -------------------------------------------------

  const gradient_index_A = hash(A_square_x, A_square_y) & 15;
  const gradient_index_B = hash(B_square_x, B_square_y) & 15;
  const gradient_index_C = hash(C_square_x, C_square_y) & 15;

  // -----------------------
  // -- Influence kernels --
  // -----------------------

  const distance_A_squared = delta_A_x * delta_A_x + delta_A_y * delta_A_y;
  const distance_B_squared = delta_B_x * delta_B_x + delta_B_y * delta_B_y;
  const distance_C_squared = delta_C_x * delta_C_x + delta_C_y * delta_C_y;

  let kernel_A = Math.max(0, 0.5 - distance_A_squared);
  let kernel_B = Math.max(0, 0.5 - distance_B_squared);
  let kernel_C = Math.max(0, 0.5 - distance_C_squared);

  kernel_A = kernel_A ** 4;
  kernel_B = kernel_B ** 4;
  kernel_C = kernel_C ** 4;

  // -------------------------------------------------------------
  // -- Alignment between gradient vector and difference vector --
  // -------------------------------------------------------------

  const dot_A =
    GRADIENTS_16_I[gradient_index_A].x * delta_A_x +
    GRADIENTS_16_I[gradient_index_A].y * delta_A_y;
  const dot_B =
    GRADIENTS_16_I[gradient_index_B].x * delta_B_x +
    GRADIENTS_16_I[gradient_index_B].y * delta_B_y;
  const dot_C =
    GRADIENTS_16_I[gradient_index_C].x * delta_C_x +
    GRADIENTS_16_I[gradient_index_C].y * delta_C_y;

  const result = dot_A * kernel_A + dot_B * kernel_B + dot_C * kernel_C;

  // -----------------------------------------------------------------------
  // -- Magic numbers to empirically fit the output into the [0, 1] range --
  // -----------------------------------------------------------------------
  return result * 35 + 0.5;
}

const size = 600;
const scalar = 0.008;

function setupContext(canvas: HTMLCanvasElement) {
  canvas.width = canvas.height = size;

  const context = canvas.getContext("2d");
  if (!context) throw "Cannot get 2d context";

  context.fillStyle = "#111111";
  context.fillRect(0, 0, size, size);

  Canvas2D.flipY(context, size);

  return context;
}

export function simplexNoise(canvas: HTMLCanvasElement) {
  const context = setupContext(canvas);

  const ref = createNoise2D(Math.random);

  let min = Infinity;
  let max = -Infinity;
  let sum = 0;

  for (let x = 0; x < size; x++) {
    for (let y = 0; y < size; y++) {
      const value = noise(x * scalar, y * scalar);
      // const value = ref(x * scalar, y * scalar) * 0.5 + 0.5;

      if (value < min) min = value;
      if (value > max) max = value;
      sum += value;

      context.fillStyle = Colors.getRGB(0, value * 0.7, 0);
      context.fillRect(x, y, 1, 1);
    }
  }

  const average = sum / (size * size);

  console.log("min:", min);
  console.log("max:", max);
  console.log("average:", average);
}
```
