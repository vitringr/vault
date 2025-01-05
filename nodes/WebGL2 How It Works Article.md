---
tags:
  - "article"
context:
  - "[[WebGL2]]"
  - "[[WebGL Articles]]"
---

# WebGL2 How It Works Article

Reference: [WebGL2 How It Works Article](https://webgl2fundamentals.org/webgl/lessons/webgl-how-it-works.html)

Core article about [[WebGL2]].

---

Read: [[WebGL2 Fundamentals Article]]

There are two basic parts to this [[GPU]] thing:

- The first part processes vertices (or streams of data) into clip space vertices.
- The second part draws pixels based on the first part.

When you call:

```js
gl.drawArrays(gl.TRIANGLES, 0, 9);
```

the `9` there means "process 9 vertices".

1. You provide vertices.
2. The [[GLSL]] [[Vertex Shader]] gets called once for each vertex, setting the `gl_Position` value for the current vertex.
3. The GPU takes that value and stores it internally.

Assument you're drawing `TRIANGLES`, every time this generates 3 vertices the GPU uses them to rasterize (draw with pixels) a triangle.

For each pixel it will call the [[Fragment Shader]], deciding what color to make that pixel.

To pass more information from the vertex shader to the fragment shader, use [[Varying|Varyings]].

You can create a varying that passes the clip space position from the vertex shader to the fragment shader:

```glsl
#version 300 es

in vec2 a_position;

out vec2 myVarying;

uniform vec2 u_resolution;

void main() {
  vec2 clipSpace = (((a_position / u_resolution) * 2.0) - 1.0) * vec2(1, -1);

  myVarying = clipSpace;

  gl_Position = vec4(clipSpace, 0, 1);
}
```

```glsl
#version 300 es
precision highp float;

uniform vec4 u_color;

in vec2 myVarying;

out vec4 outColor;

void main() {
  outColor = u_color + vec4(myVarying, 0, 0);
}
```

WebGL will connect the varying in the vertex shader to the varying of the same name and type in the fragment shader.

Notice how the colors don't move if the shape moves. That's because they are relative to the background.

**Varying Interpolation**: The vertex shader only gets called 3 times, therefore it's only computing 3 colors, yet your triangle is many colors. This is why it's called a _varying_. WebGL _interpolates_ between the computed vertices values. For each pixel it calls the fragment shader with the interpolated value for that pixel.

So what do these buffer and attribute commands do?

Buffers are the way of getting vertex and other data onto the GPU.

`gl.createBuffer` creates a buffer.
`gl.bindBuffer` sets that buffer as the buffer to be worked on.
`gl.bufferData` copies data into the current buffer.

Once the data is in the buffer you need to tell WebGL how exactly to use the data.

You should have the locations of the GLSL variables stored somewhere:

```js
const aPositionLocation = gl.getAttribLocation(program, "a_position");
const aColorLocation = gl.getAttribLocation(program, "a_color");
const uResolutionLocation = gl.getUniformLocation(program, "u_resolution");
const uColorLocation = gl.getUniformLocation(program, "u_color");
```

> [!Warning] Unused Variables
> The [[GLSL]] [[Shader]] program can optimize itself for unused variables. This can cause an error if you attempt to get the location of such variable.

Once you know the location of an attribute you can issue two commands.

Command to tell WebGL you want to supply data from a buffer:

```js
gl.enableVertexAttribArray(variableLocation);
```

Command to tell WebGL to get data from the buffer last bound with `gl.bindBuffer`. Also specifies how exactly to read the data:

```js
gl.vertexAttribPointer(
  variableLocation,
  numComponents, // 1 - 4
  typeOfData,
  normalizeFlag,
  strideToNextPieceOfData,
  offsetInfoBuffer,
);
```

> [!Tip] Stride and Offset to 0
> If you are using 1 buffer per type of data then both stride and offset can always be `0`. Setting them for values other than `0` would only be worth in a serious nitpicking scenario.
