---
tags:
  - "article"
context:
  - "[[WebGL2]]"
  - "[[WebGL Articles]]"
---

# WebGL2 Hello World Article

Reference: [WebGL2 Fundamentals Article](https://webgl2fundamentals.org/webgl/lessons/webgl-fundamentals.html)

Continuation of the [[WebGL2 Fundamentals Article]] with example setup.

---

WebGL only cares about 2 things: **clip space coordinates** and **colors**.

The job of the programmer using WebGL is to provide it with those 2 things. You provide your two shaders to do this. A vertex shader to provide clip space coordinates, and a fragment shader to provide the color.

Clip space coordinates always go from `-1` to `+1` no matter what size the canvas is.
Colors go from `0` to `1`.

Simple WebGL Example:

**Vertex Shader**:

```glsl
#version 300 es

// An attribute is an input (in) to a vertex shader. It will receive data from a buffer.
in vec4 a_position;

// All shaders have a main function
void main() {
    // gl_Position is a special variable the vertex shader is responsible for setting.
    gl_Position = a_position;
}
```

**Fragment Shader**:

```glsl
#version 300 es

// Fragment shaders don't have a default precision so we need to pick one.
// highp is a good default. It means "high precision".
precision highp float;

// We need to declare an output for the fragment shader.
out vec4 outColor;

void main() {
    // Setting the output to a constant reddish-purple.
    outColor = vec4(1, 0, 0.5, 1);
}
```

To get started with WebGL, first we need an HTML canvas element:

```html
<canvas id="drawing"></canvas>
```

Then in [[JavaScript]] we can look it up:

```js
const canvas = document.getElementById("drawing");
```

and create the `WebGL2RenderingContext`:

```js
const gl = canvas.getContext("webgl2");
if (!gl) throw new Error("no webgl2 for you!");
```

Now we need to compile the shaders to put them on the GPU so first we need to get them into strings. You can create GLSL strings any way you normally create strings in JavaScript.

> [!Tip] Generated Shaders
> Most 3D engines generate [[GLSL]] [[Shader|Shaders]] on the fly using various types of templates, concatenation, etc.

> [!Warning] First Line Version
> The `#version 300 es` line MUST BE THE VERY FIRST LINE OF YOUR SHADER. No comments or blank lines are allowed before it! It tells WebGL2 you want to use WebGL2's shader language called GLSL ES 3.00. If you don't put that as the first line the shader language will default to WebGL 1.0's GLSL ES 1.00, which has many differences and far less features.

Next we need a function that will create a shader, upload the GLSL source, and compile the shader:

```js
function createShader(gl, type, source) {
  const shader = gl.createShader(type);
  gl.shaderSource(shader, source);
  gl.compileShader(shader);

  const success = gl.getShaderParameter(shader, gl.COMPILE_STATUS);
  if (success) return shader;

  console.error(gl.getShaderInfoLog(shader));
  gl.deleteShader(shader);
}
```

We can now call that function to create the 2 shaders:

```js
const vertexShader = createShader(gl, gl.VERTEX_SHADER, vertexShaderSource);
const fragmentShader = createShader(
  gl,
  gl.FRAGMENT_SHADER,
  fragmentShaderSource,
);
```

We then need to link those 2 shaders into a program:

```js
function createProgram(gl, vertexShader, fragmentShader) {
  const program = gl.createProgram();

  gl.attachShader(program, vertexShader);
  gl.attachShader(program, fragmentShader);

  gl.linkProgram(program);

  const success = gl.getProgramParameter(program, gl.LINK_STATUS);
  if (success) return program;

  console.error(gl.getProgramInfoLog(program));
  gl.deleteProgram(program);
}
```

And call it:

```js
const program = createProgram(gl, vertexShader, fragmentShader);
```

Now that we've created a GLSL program on the GPU we need to supply data to it.

The majority of the WebGL API is about setting up state to supply data to our GLSL programs.

In this case our only input to our GLSL program is `a_position` which is an attribute. The first thing we should do is look up the location of the attribute:

```js
const positionAttributeLocation = gl.getAttribLocation(program, "a_position");
```

Looking up attribute locations (and uniform locations) is something you should do during initialization, not in your render loop.

Attributes get their data from buffers so we need to create a buffer:

```js
const positionBuffer = gl.createBuffer();
```

WebGL lets us manipulate many WebGL resources on _global bind points_. You can think of bind points as internal global variables inside WebGL. First you bind a resource to a bind point, then all other functions refer to the resource through the bind point.

So lets bind the position buffer to the `gl.ARRAY_BUFFER` bind point:

```js
gl.bindBuffer(gl.ARRAY_BUFFER, positionBuffer);
```

Now we can put data in that buffer by referencing it through the bind point:

```js
// Three 2D points
const positions = [0, 0, 0, 0.5, 0.7, 0];

gl.bufferData(gl.ARRAY_BUFFER, new Float32Array(positions), gl.STATIC_DRAW);
```

First we created the `positions` JavaScript array.

Since WebGL needs strongly typed data, we convert them to a 32bit floating point array `new Float32Array(positions)`.

Then `gl.bufferData` copies the data to the `positionBuffer` on the GPU. It's using the position buffer because we bound it to the `ARRAY_BUFFER` bind point above.

The last argument, `gl.STATIC_DRAW` is a hint to WebGL about how the data is going to be used. WebGL will try to use that hint to optimize certain things. `gl.STATIC_DRAW` tells WebGL we are not likely to change this data much.

Now that we've put data in a buffer we need to tell the attribute how to get data out of it. First we need to create a collection of attribute state called _Vertex Array Object (VAO)_:

```js
const vao = gl.createVertexArray();
```

And we need to make that the current vertex array so that all of our attribute settings will apply to that set of attribute state:

```js
gl.bindVertexArray(vao);
```

Now we finally setup the attributes in the vertex array. First off we need to turn the attribute on. This tells WebGL we want to get data out of a buffer. If we don't turn on the attribute then the attribute will have a constant value.

```js
gl.enableVertexAttribArray(positionAttributeLocation);
```

Then we need to specify how to pull the data out:

```js
const size = 2; // 2 components per iteration.
const type = gl.FLOAT; // Data is 32bit floats.
const normalize = false; // Don't normalize the data.
const stride = 0; // 0 = move forward size * sizeof(type) each iteration.
const offset = 0; // Start at the beginning of the buffer.

gl.vertexAttribPointer(
  positionAttributeLocation,
  size,
  type,
  normalize,
  stride,
  offset,
);
```

A hidden part of `gl.vertexAttribPointer` is that it binds the current `ARRAY_BUFFER` to the attribute. In other words now this attribute is bound to `positionBuffer`. That means we're free to bind something esle to the `ARRAY_BUFFER` bind point. The attribute will continue to use the `positionBuffer`.

Note that from the point of view of our GLSL vertex shader the `a_position` attribute is a `vec4` (Vector 4).

```glsl
in vec4 a_position;
```

`vec4` is a 4 float value. In JavaScript terms it would look something like `a_position = {x: 0, y: 0, z: 0, w: 0}`.

Above we set `size = 2`. Attributes default to `0, 0, 0, 1` so this attribute will get its first 2 values (`x` and `y`) from our buffer. The `z` and `z` will be the default `0` and `1` respectively.

Before we draw we should resize the HTML canvas to match its display size. Canvases just like images have 2 sizes - the number of pixels in them, and separately the size they are displayed. CSS determines the size the canvas is displayed.

> [!Tip]
> You should always set the size of a [[Canvas Element (HTML)|canvas]] with [[CSS]] since it's far far more flexible than any other method.

To make the number of pixels in the canvas match the size its displayed you can use a helper function:

```ts
function resizeCanvasToDisplaySize(
  canvas: HTMLCanvasElement,
  multiplier?: number,
): boolean {
  const scale = multiplier || 1;

  const width = (canvas.clientWidth * scale) | 0;
  const height = (canvas.clientHeight * scale) | 0;

  const needsResize = !(canvas.width === width && canvas.height === height);

  if (needsResize) {
    canvas.width = width;
    canvas.height = height;
  }

  return needsResize;
}
```

Let the CSS determine the size and then adjust to match:

```js
webGLUtils.resizeCanvasToDisplaySize(gl.canvas);
```

We need to tell WebGL how to convert from the clip space values wel'll be setting `gl_Position` to back into pixels (aka. screen space).

To do this we call `gl.viewport` and pass it the current size of the canvas:

```js
gl.viewport(0, 0, gl.canvas.width, gl.canvas.height);
```

This tells WebGL the `-1` <-> `+1` clip space maps to `0` <-> `gl.canvas.width` for `x` and `0` <-> `gl.canvas.height` for `y`.

We clear the canvas. `0, 0, 0, 0` are red, green, blue, and alpha respectively, so in this case we're making the canvas transparent:

```js
// Clear the canvas.
gl.clearColor(0, 0, 0, 0);
gl.clear(gl.COLOR_BUFFER_BIT);
```

Next we need to tell WebGL which shader program to execute:

```js
// Tell it to use our program (pair of shaders).
gl.useProgram(program);
```

Then we need to tell it which set of buffers to use and how to pull data out of those buffers to supply the attributes:

```js
// Bind the attribute/buffer set we want.
gl.bindVertexArray(vao);
```

After all of that we can finally ask WebGL to execute our GLSL program:

```js
const primitiveType = gl.TRIANGLES;
const offset = 0;
const count = 3;

gl.drawArrays(primitiveType, offset, count);
```

Because the `count` is `3` this will execute our vertex shader 3 times. The first time `a_position.x` and `a_position.y` in our vertex shader attribute will be set to the first 2 values from the `positionBuffer`. The second time `a_position.xy` will be set to the second two values. The last time it will be set to the last two values.

Because we set `primitiveType` to `gl.TRIANGLES`, each time our vertex shader is run 3 times WebGL will draw a triangle based on the 3 values we set `gl_Position` to. No matter what size our canvas is those values are in clip space coordinates that go from `-1` to `+1` in each direction.

Because our vertex shader is simply copying our `positionBuffer` values to `gl_Position` the triangle will be drawn at clip space coordinates:

```
0,   0,
0,   0.5,
0.7, 0
```

Converting from clip space to screen space if the canvas size happened to be `400x300` we'd get something like this:

| clip space | screen space |
| ---------- | ------------ |
| `0,   0`   | `200,   150` |
| `0,   0.5` | `200,   225` |
| `0.7, 0`   | `340,   150` |

WebGL will now render that triangle. For every pixel it is about to draw WebGL will call our fragment shader. Our fragmentShader just sets `outColor` to `1, 0, 0.5, 1`. Since the canvas is an 8bit per channel canvas that means WebGL is going to write the values `[255, 0, 127, 255]` into the canvas.

Success!

## Clip Space to Screen Space

For 2D stuff you would probably rather work in pixels than clip space.

We can supply the position in pixels and have the vertex shader convert it to clip space:

```glsl
in vec2 a_position;

uniform vec2 u_resolution;

void main() {
    // convert the position from pixels to 0.0 to 1.0
    vec2 zeroToOne = a_position / u_resolution;

    // convert from 0->1 to 0->2
    vec2 zeroToTwo = zeroToOne * 2.0;

    // convert from 0->2 to -1->+1 (clip space)
    vec2 clipSpace = zeroToTwo - 1.0;

    gl_Position = vec4(clipSpace, 0, 1);
}
```

We changed the `a_position` to a `vec2` since we're only using `x` and `y` anyway.

Next we added a uniform called `u_resolution`. To set that we need to look up its location:

```js
const resolutionUniformLocation = gl.getUniformLocation(
  program,
  "u_resolution",
);
```

The rest should be clear from the comments.

By setting `u_resolution` to the resolution of our canvas the shader will now take the positions we put in `positionBuffer` supplied in pixels coordinates and convert them to clip space.

Now we can change our position values from clip space to pixels. This time we're going to draw a rectangle made from 2 triangles:

```js
// Two triangles, 3 points each.
const positions = [0, 0, 80, 20, 10, 30, 10, 30, 80, 20, 80, 30];

gl.bufferData(gl.ARRAY_BUFFER, new Float32Array(positions), gl.STATIC_DRAW);
```

After we set which program to use we can set the value for the uniform we created.

> [!Note]
> The `gl.useProgram` is like `gl.bindBuffer` in that it sets the current program. After that all the `gl.uniformXXX` functions set uniforms on the current program.

```js
gl.useProgram(program);

// Pass the canvas resolution to convert from pixels to clip space in the shader.
gl.uniform2f(resolutionUniformLocation, gl.canvas.width, gl.canvas.height);
```

And since there are 2 triangles now we need to have WebGL call our vertex shader 6 times so we need to change the `count` to `6`:

```js
gl.drawArrays(gl.TRIANGLES, 0, 6);
```

Success!

## Vertical Y Direction

WebGL considers positive `y` as up and negative `y` as down.

In clip space the bottom left corner is `[-1, -1]`.

To get it to the more traditional top left corner used for 2D graphics we can flip the clip space `y` coordinate:

```glsl
gl_Position = vec4(clipSpace * vec2(1, -1), 0, 1);
```

We can simplify everything from clip space conversion to vertical flip in one line like:

```glsl
  vec2 clipSpace = (((a_position / u_resolution) * 2.0) - 1.0) * vec2(1, -1);

  gl_Position = vec4(clipSpace, 0, 1);
```

Read: [[WebGL2 How It Works Article]]
