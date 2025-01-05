---
tags:
  - "article"
context:
  - "[[WebGL2]]"
  - "[[WebGL Articles]]"
---

# WebGL2 Fundamentals Article

Reference: [WebGL2 Fundamentals Article](https://webgl2fundamentals.org/webgl/lessons/webgl-fundamentals.html)

Core article about [[WebGL2]].

---

**Backwards Compatibility**:
[[WebGL2]] is nearly 100% backward compatible with [[WebGL|WebGL1]].

**Rasterization Engine**:
Draws points, lines, and triangles based on supplied code.

**GPU & Shaders**:
WebGL runs on the [[GPU]]. As such it needs code that runs on that GPU. A pair of [[Function (Programming)|Functions]], called a _[[Vertex Shader]]_ and a _[[Fragment Shader]]_, written in [[GLSL]]. Paired together they are called a _program_.

**Vertex and Fragment Shader**:
The vertex shader computes vertex positions. Based on these positions WebGL can then rasterize various primitives, including points, lines, or triangles.

When rasterizing these primitives it calls the fragment shader, which computes the color for each pixel of the primitive currently being drawn.

**State Paradigm**:
Nearly all of the entire WebGL API is about setting up state for these shader functions to run.

For each thing you want to draw you setup a bunch of state and then execute a pair of functions which executes your shaders on the GPU.

**Shader Data**:
Any data you want your shaders to have access to must be provided to the GPU.

There are 4 ways a shader can receive data:

1. **Attributes, Buffers, and Vertex Arrays**:
   _Buffers_ are arrays of binary data you upload to the GPU. Buffers are not random access.

   _Attributes_ are used to to specify how to pull data out of the buffers and provide it to the vertex shader.

   The state of attributes, which buffers to use for each one, and how to pull out data from those buffers is collected into a _vertex array object (VAO)_.

2. **Uniforms**:
   _Uniforms_ are effectively global variables you set before you execute your shader program.

3. **Textures**:
   _Textures_ are arrays of data you can randomly access in your shader program.

   The most common thing to put in a texture is image data, but textures are just data and can just as easily contain something other than colors.

4. **Varyings**:
   _[[Varying|Varyings]]_ are a way for a vertex shader to pass data to a fragment shader.

   Depending on what is being rendered (points, lines, or triangles), the values set on a varying by a vertex shader will be interpolated while executing the fragment shader.

Read: [[WebGL2 Hello World Article]]
