---
context:
  - "[[WebGL]]"
---

# WebGL Attribute

In WebGL, attributes are variables in the [[Vertex Shader]] that receive _per-vertex data_ from [[GPU Buffer|Buffers]].

---

**GLSL**: Defined as a variable in [[GLSL]].

**Buffers**: Memory area on the GPU. Arrays of data are uploaded and stored in this area.

**Attributes**: Specify how to pull data out of the buffers and provide it to the vertex shader.

```js
// Create buffer
const buffer = gl.createBuffer();

// Fill with data
gl.bindBuffer(gl.ARRAY_BUFFER, buffer);
gl.bufferData(gl.ARRAY_BUFFER, someData, gl.STATIC_DRAW);

// Look up the location on the shader
const attributeLocation = gl.getAttribLocation(someShaderProgram, "a_test");

// Tell WebGL how to pull data out of
// the buffers and into the attribute
gl.enableVertexAttribArray(attributeLocation);
gl.vertexAttribPointer(attributeLocation, 3, gl.GLOAT, false, 0, 0);
```
