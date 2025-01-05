---
tags:
  - "code"
context:
  - "[[WebGL2]]"
---

# WebGL2 Example

## Library

```ts
export class WebGL {
  static readonly setup = {
    compileShader: (
      gl: WebGL2RenderingContext,
      type: GLenum,
      source: string,
    ) => {
      const shader = gl.createShader(type);
      if (!shader) throw new Error("Unable to create shader");

      gl.shaderSource(shader, source);
      gl.compileShader(shader);

      if (!gl.getShaderParameter(shader, gl.COMPILE_STATUS)) {
        const info = gl.getShaderInfoLog(shader);
        gl.deleteShader(shader);
        throw new Error("Could not compile shader: " + info);
      }

      return shader;
    },

    linkProgram: (
      gl: WebGL2RenderingContext,
      vertexShader: WebGLShader,
      fragmentShader: WebGLShader,
    ) => {
      const program = gl.createProgram();
      if (!program) throw new Error("Unable to create program");

      gl.attachShader(program, vertexShader);
      gl.attachShader(program, fragmentShader);

      gl.linkProgram(program);

      if (!gl.getProgramParameter(program, gl.LINK_STATUS)) {
        const info = gl.getProgramInfoLog(program);
        gl.deleteProgram(program);
        throw new Error("Program failed to link: " + info);
      }

      return program;
    },

    cleanup: (
      gl: WebGL2RenderingContext,
      program: WebGLProgram,
      shaders: WebGLShader[],
    ) => {
      shaders.forEach((shader) => gl.deleteShader(shader));
      gl.deleteProgram(program);
    },
  };

  static readonly utils = {
    resizeCanvasToDisplaySize: (
      canvas: HTMLCanvasElement,
      multiplier?: number,
    ): boolean => {
      const scale = multiplier || 1;

      const width = (canvas.clientWidth * scale) | 0;
      const height = (canvas.clientHeight * scale) | 0;

      const needsResize = !(canvas.width === width && canvas.height === height);

      if (needsResize) {
        canvas.width = width;
        canvas.height = height;
      }

      return needsResize;
    },

    clear: (
      gl: WebGL2RenderingContext,
      red: number,
      green: number,
      blue: number,
      alpha: number,
    ) => {
      gl.clearColor(red, green, blue, alpha);
      gl.clear(gl.COLOR_BUFFER_BIT);
    },
  };

  static readonly shapes = {
    rectangle: (
      x: number,
      y: number,
      width: number,
      height: number,
    ): number[] => {
      const x1 = x;
      const x2 = x + width;
      const y1 = y;
      const y2 = y + height;

      return [x1, y1, x2, y1, x1, y2, x1, y2, x2, y1, x2, y2];
    },
  };
}
```

## Setup

```ts
const gl = canvasRef.getContext("webgl2");
if (!gl) throw new Error("Failed to get WebGL2 context");

const vertexShader = WebGL.setup.compileShader(
  gl,
  gl.VERTEX_SHADER,
  vertexShader,
);
const fragmentShader = WebGL.setup.compileShader(
  gl,
  gl.FRAGMENT_SHADER,
  fragmentShader,
);
const program = WebGL.setup.linkProgram(gl, vertexShader, fragmentShader);

WebGL.utils.resizeCanvasToDisplaySize(gl.canvas as HTMLCanvasElement);
gl.viewport(0, 0, gl.canvas.width, gl.canvas.height);

mainProgram(gl, program);

onCleanup(() =>
  WebGL.setup.cleanup(gl, program, [vertexShader, fragmentShader]),
);
```

## Shaders

**Vertex Shader**:

```glsl
#version 300 es

in vec2 a_position;
in vec4 a_color;

uniform vec2 u_resolution;

out vec2 v_clipSpace;
out vec4 v_color;

void main() {
    // Fix the clip space to go from [0, 0] to [1, 1].
    vec2 clipSpace = (((a_position / u_resolution) * 2.0) - 1.0) * vec2(1, -1);

    v_clipSpace = clipSpace;
    v_color = a_color;

    gl_Position = vec4(clipSpace, 0, 1);
}
```

**Fragment Shader**:

```glsl
#version 300 es
precision highp float;

uniform vec4 u_color;

in vec2 v_clipSpace;
in vec4 v_color;

out vec4 outColor;

void main() {
  outColor = u_color + vec4(v_clipSpace, 0.5, 0) + v_color.yxzw;
}
```

## Program

```ts
/* Find the variable locations from the GLSL program. */
const aPositionLocation = gl.getAttribLocation(program, "a_position");
const aColorLocation = gl.getAttribLocation(program, "a_color");

const uResolutionLocation = gl.getUniformLocation(program, "u_resolution");
const uColorLocation = gl.getUniformLocation(program, "u_color");

/* Create a collection of attribute state called a Vertex Array Object. */
const vao = gl.createVertexArray();
/* And make it the current vertex array so that attribute settings apply to it. */
gl.bindVertexArray(vao);

/* Attributes get their data from buffers. Creating one here. */
const positionBuffer = gl.createBuffer();
/* Bind the buffer to the global ARRAY_BUFFER bind point. */
gl.bindBuffer(gl.ARRAY_BUFFER, positionBuffer);
/* Insert the data into the buffer by referencing it through the bind point. */
const rectangleVertices = WebGL.shapes.rectangle(
  10,
  10,
  gl.canvas.width - 20,
  gl.canvas.height - 20,
);
gl.bufferData(
  gl.ARRAY_BUFFER,
  new Float32Array(rectangleVertices),
  gl.STATIC_DRAW,
);
/* Enable the attribute. This tells WebGL you want to get data out of a buffer. */
gl.enableVertexAttribArray(aPositionLocation);
/* Specify how to pull the data out. */
gl.vertexAttribPointer(aPositionLocation, 2, gl.FLOAT, false, 0, 0);

/* Same thing for another attribute. */
const colorBuffer = gl.createBuffer();
gl.bindBuffer(gl.ARRAY_BUFFER, colorBuffer);
const colors = [
  0.7, 0, 0, 1, 0.7, 0, 0, 1, 0.7, 0, 0, 1, 0, 0.7, 0, 1, 0, 0.7, 0, 1, 0, 0.7,
  0, 1,
];
gl.bufferData(gl.ARRAY_BUFFER, new Float32Array(colors), gl.STATIC_DRAW);
gl.enableVertexAttribArray(aColorLocation);
gl.vertexAttribPointer(aColorLocation, 4, gl.FLOAT, false, 0, 0);

/* Tell WebGL which program to execute. Also sets state for the uniforms below. */
gl.useProgram(program);
gl.bindVertexArray(vao);

/* After gl.useProgram, push data into the uniforms. */
gl.uniform2f(uResolutionLocation, gl.canvas.width, gl.canvas.height);
gl.uniform4f(uColorLocation, 0, 0, 0, 1);

/* Clear before drawing. */
WebGL.utils.clear(gl, 0, 0, 0, 0);
/* Draw call. Specify mode and vertices count. */
gl.drawArrays(gl.TRIANGLES, 0, 6);
```
