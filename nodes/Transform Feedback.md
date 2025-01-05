---
aliases:
  - Stream Output
context:
  - "[[General Purpose GPU]]"
---

# Transform Feedback

Concept/feature for capturing the output of a [[Vertex Shader]] into [[Data Buffer]] objects, bypassing the [[Fragment Shader]] stage.

---

**General Purpose**: Useful for [[General Purpose GPU]] scenarios to process arbitrary data.

**Feedback Loops**: Useful for [[Feedback|Feedback Loops]] in rendering, where the output of one pass becomes the input of another.

**Pipeline**:

1. **Input**: Data is processed by the vertex shader.
2. **Processing**: The vertex shader modifies the data.
3. **Output**: The data is written into data buffer object instead of being rasterized into fragments.

**Storage**: Stores transformed data directly in [[GPU]] memory. This avoids the round trip of reading data back to the [[CPU]], which is slow.

**Compute Shaders**: Transform feedback is useful in engines that don't support [[Compute Shader|Compute Shaders]].
