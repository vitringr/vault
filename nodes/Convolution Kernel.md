---
context:
  - "[[Computer Graphics]]"
---

# Convolution Kernel

Small fixed [[Matrix]] used to apply convolution operations on input data.

Useful for extracting features like edges, textures, and patterns.

---

**Function**: When each pixel in the output image is a function of the nearby pixels (including self) in the input image - the kernel is that function.

**Matrix Size**: Kernels are generally fixed `3x3` or `5x5` [[Matrix|matrices]].

**Visual Matrix**:

|     |      |      |      |     |
| --- | ---- | ---- | ---- | --- |
| 35  | 40   | 41   | 45   | 50  |
| 40  | _40_ | _42_ | _46_ | 52  |
| 42  | _46_ | _50_ | _55_ | 55  |
| 48  | _52_ | _56_ | _58_ | 60  |
| 56  | 60   | 65   | 70   | 75  |

x

|     |     |     |
| --- | --- | --- |
| 0   | 1   | 0   |
| 0   | 0   | 0   |
| 0   | 0   | 0   |

=

|     |     |     |     |     |
| --- | --- | --- | --- | --- |
| ?   | ?   | ?   | ?   | ?   |
| ?   | ?   | ?   | ?   | ?   |
| ?   | ?   | 42  | ?   | ?   |
| ?   | ?   | ?   | ?   | ?   |
| ?   | ?   | ?   | ?   | ?   |

**Normalization**: The sum can be divided by the weight of the kernel:

```ts
const computeKernelWeight = (kernel: number[]) => {
  const weight = kernel.reduce((prev, curr) => prev + curr);
  return weight <= 0 ? 1 : weight;
};
```

**Examples**:

- [[Identity Kernel]]
- [[Blur Kernel]]
- [[Emboss Kernel]]
- [[Sharpening Kernel]]
- [[Edge Detection Kernel]]
- [[Horizontal Edge Detection Kernel]]
- [[Vertical Edge Detection Kernel]]
