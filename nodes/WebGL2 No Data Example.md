---
tags:
  - "code"
context:
  - "[[WebGL2]]"
---

# WebGL2 No Data Example

Some simple examples using the [[Vertex Shader]] to draw without data.

## Shadertoy

TypeScript:

```ts
import { WebGL } from "../../webgl";
import vertex from "./vertex.glsl";
import fragment from "./fragment.glsl";
export class Shadertoy {
  constructor(private readonly canvas: HTMLCanvasElement) {}

  readonly start = () => {
    const gl = this.canvas.getContext("webgl2");
    if (!gl) throw new Error("Failed to get WebGL2 context");

    const vertexShader = WebGL.setup.compileShader(
      gl,
      gl.VERTEX_SHADER,
      vertex,
    );
    const fragmentShader = WebGL.setup.compileShader(
      gl,
      gl.FRAGMENT_SHADER,
      fragment,
    );
    const program = WebGL.setup.linkProgram(gl, vertexShader, fragmentShader);

    WebGL.utils.resizeCanvasToDisplaySize(gl.canvas as HTMLCanvasElement);
    gl.viewport(0, 0, gl.canvas.width, gl.canvas.height);

    this.main(gl, program);
  };

  private readonly main = (
    gl: WebGL2RenderingContext,
    program: WebGLProgram,
  ) => {
    const aPositionLocation = gl.getAttribLocation(program, "a_position");

    const uResolutionLocation = gl.getUniformLocation(program, "u_resolution");

    let pointerX: number = 0;
    let pointerY: number = 0;
    const uPointerLocation = gl.getUniformLocation(program, "u_pointer");

    let time: number = 0;
    const uTimeLocation = gl.getUniformLocation(program, "u_time");

    const vao = gl.createVertexArray();
    gl.bindVertexArray(vao);

    const positionBUffer = gl.createBuffer();
    gl.bindBuffer(gl.ARRAY_BUFFER, positionBUffer);
    const rectanglePoints = WebGL.shapes.rectangle(
      0,
      0,
      gl.canvas.width,
      gl.canvas.height,
    );
    gl.bufferData(
      gl.ARRAY_BUFFER,
      new Float32Array(rectanglePoints),
      gl.STATIC_DRAW,
    );
    gl.enableVertexAttribArray(aPositionLocation);
    gl.vertexAttribPointer(aPositionLocation, 2, gl.FLOAT, false, 0, 0);

    gl.useProgram(program);
    gl.bindVertexArray(vao);

    const canvasBounds = this.canvas.getBoundingClientRect();
    this.canvas.addEventListener("mousemove", (ev: MouseEvent) => {
      pointerX = ev.clientX - canvasBounds.left;
      pointerY = ev.clientY - canvasBounds.top;
    });

    const render = () => {
      time += 0.001;

      gl.uniform2f(uResolutionLocation, gl.canvas.width, gl.canvas.height);
      gl.uniform2f(uPointerLocation, pointerX, pointerY);
      gl.uniform1f(uTimeLocation, time);

      WebGL.utils.clear(gl, 1);

      gl.drawArrays(gl.TRIANGLES, 0, 6);

      requestAnimationFrame(render);
    };

    requestAnimationFrame(render);
  };
}
```

Vertex Shader:

```glsl
#version 300 es

in vec2 a_position;

uniform vec2 u_resolution;

void main() {
  vec2 clipSpace = (((a_position / u_resolution) * 2.0) - 1.0) * vec2(1, -1);

  gl_Position = vec4(clipSpace, 0, 1);
}
```

Fragment Shader:

```glsl
#version 300 es

precision highp float;

#define PI radians(180.0)
#define TAU radians(360.0)

uniform vec2 u_resolution;
uniform vec2 u_pointer;
uniform float u_time;

out vec4 outColor;

void main() {
  float xPointerValue = u_pointer.x / u_resolution.x;
  float yPointerValue = u_pointer.y / u_resolution.y;
  float pointerValue = xPointerValue / 2.0 + yPointerValue / 2.0;

  float wave = sin(fract(u_time) * PI);

  outColor = vec4(
    pointerValue,
    wave,
    gl_FragCoord.x / u_resolution.x,
    1
  );
}
```

## Circle out of Points

TypeScript:

```ts
export const noData: IGraphicWebGL2 = {
  vertexShader: vertex,
  fragmentShader: fragment,

  mainProgram: (gl, program) => {
    const numVerts = 20;

    const uNumVertsLocation = gl.getUniformLocation(program, "u_numVerts");
    const uResolutionLocation = gl.getUniformLocation(program, "u_resolution");

    gl.useProgram(program);

    gl.uniform1i(uNumVertsLocation, numVerts);
    gl.uniform2f(uResolutionLocation, gl.canvas.width, gl.canvas.height);

    gl.drawArrays(gl.POINTS, 0, numVerts);
  },
};
```

Vertex Shader:

```glsl
#version 300 es

uniform int u_numVerts;
uniform vec2 u_resolution;

#define PI radians(180.0)
#define TAU radians(360.0)

void main() {
  float aspect = u_resolution.y / u_resolution.x;

  float index = float(gl_VertexID) / float(u_numVerts); // goes from 0 to 1
  float angle = index * TAU;
  float radius = 0.8;

  float x = cos(angle) * radius * aspect;
  float y = sin(angle) * radius;

  gl_Position = vec4(x, y, 0, 1);
  gl_PointSize = 5.0;
}
```

Fragment Shader:

```glsl
#version 300 es
precision highp float;

out vec4 outColor;

void main() {
  outColor = vec4(0, 1, 1, 1);
}
```

## Particle Rain

TypeScript:

```ts
export const noData: IGraphicWebGL2 = {
  vertexShader: vertex,
  fragmentShader: fragment,

  mainProgram: (gl, program) => {
    const numVerts = 300;
    const timeIncrement = 0.001;

    const uNumVertsLocation = gl.getUniformLocation(program, "u_numVerts");
    const uResolutionLocation = gl.getUniformLocation(program, "u_resolution");
    const uTimeLocation = gl.getUniformLocation(program, "u_time");

    gl.useProgram(program);
    gl.uniform1i(uNumVertsLocation, numVerts);
    gl.uniform2f(uResolutionLocation, gl.canvas.width, gl.canvas.height);

    let time = 0;
    const update = () => {
      time += timeIncrement;
      gl.uniform1f(uTimeLocation, time);

      gl.drawArrays(gl.POINTS, 0, numVerts);

      requestAnimationFrame(update);
    };

    requestAnimationFrame(update);
  },
};
```

Vertex Shader:

```glsl
#version 300 es

uniform int u_numVerts;
uniform vec2 u_resolution;
uniform float u_time;

#define PI radians(180.0)
#define TAU radians(360.0)

float random(float p) {
  vec2 p2 = fract(vec2(p * 5.3983, p * 5.4427));
  p2 += dot(p2.yx, p2.xy + vec2(21.5351, 14.3137));
  return fract(p2.x * p2.y * 95.4337);
}

void main() {
  float aspect = u_resolution.y / u_resolution.x;

  float index = float(gl_VertexID) / float(u_numVerts); // goes from 0 to 1
  float angle = index * TAU;
  float radius = 0.8;

  float x = random(index) * 2.0 - 1.0;
  float y = fract(index + u_time) * -2.0 + 1.0;

  gl_Position = vec4(x, y, 0, 1);
  gl_PointSize = 2.0;
}
```

Fragment Shader:

```glsl
#version 300 es
precision highp float;

out vec4 outColor;

void main() {
  outColor = vec4(0, 1, 1, 1);
}
```
