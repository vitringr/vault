---
context:
  - "[[WebGL]]"
---

# WebGL Uniforms

Global variables in [[Shader|Shaders]] that provide _constant data_ for a draw call.

---

**GLSL**: Declared with `uniform` in [[GLSL]].

**Set**: Set from the [[CPU]] using functions like `gl.uniform1f`.

**Global**: Constant and shared across all vertices and fragments in a single draw call.
