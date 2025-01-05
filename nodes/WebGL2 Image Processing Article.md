---
tags:
  - "article"
context:
  - "[[WebGL2]]"
  - "[[WebGL Articles]]"
---

# WebGL2 Image Processing Article

Reference: [WebGL2 Image Processing Article](https://webgl2fundamentals.org/webgl/lessons/webgl-image-processing.html)

Article about image processing in [[WebGL2]].

---

**Textures**:
To draw images in WebGL we need to use [[WebGL Texture|Textures]]. WebGL generally expects texture coordinates when reading a texture. Texture coordinates go from `0.0` to `1.0` no matter the dimensions of the texture.

WebGL2 adds the ability to read a texture using pixel coordinates as well.

**Coordinates**:
Since we're only drawing a rectangle (2 triangles) we need to tell WebGL which place in the texture each point in the rectangle corresponds to. We'll pass this information from the [[Vertex Shader]] to the [[Fragment Shader]] using a [[Varying]].

We pass texture coordinates to the vertex shader, and from it to the fragment shader:

```glsl
...

in vec2 a_textureCoordinates;

out vec2 v_textureCoordinates;

void main() {
    ...

    // Passing the textureCoordinates to the fragment shader.
    // The GPU will interpolate this value between points.
    v_textureCoordinates = a_textureCoordinates;
}
```

Then we supply a fragment shader to look up colors from the texture:

```glsl
#version 300 es
precision highp float;

// Our texture.
uniform sampler2D u_image;

// Coordinates passed from the vertex shader.
in vec2 v_textureCoordinates;

out vec4 outColor;

void main() {
    // Look up a color from the texture.
    outColor = texture(u_image, v_textureCoordinates);
}
```

Then we need to load an image, create a terxture and copy the image into the texture. Use async to wait for the image to load:

```ts
function main() {
  const image = new Image();
  image.src = "https://some/accessible/image";
  image.onload = function () { ... };
}

// ...

const aPositionLocation = gl.getAttribLocation(program, "a_position");
const aTextureCoordinatesLocation = gl.getAttribLocation(program, "a_textureCoordinates");

const uResolutionLocation = gl.getUniformLocation(program, "u_resolution");
const uPointerLocation = gl.getUniformLocation(program, "u_pointer");
const uTimeLocation = gl.getUniformLocation(program, "u_time");
const uImageLocation = gl.getUniformLocation(program, "u_image");

const vao = gl.createVertexArray();
gl.bindVertexArray(vao);

// aPosition
gl.bindBuffer(gl.ARRAY_BUFFER, gl.createBuffer());
gl.bufferData(
  gl.ARRAY_BUFFER,
  new Float32Array(
    WebGL.points.rectangle(0, 0, gl.canvas.width, gl.canvas.height),
  ),
  gl.STATIC_DRAW,
);
gl.enableVertexAttribArray(aPositionLocation);
gl.vertexAttribPointer(aPositionLocation, 2, gl.FLOAT, false, 0, 0);

// aTextureCoordinates
gl.bindBuffer(gl.ARRAY_BUFFER, gl.createBuffer());
gl.bufferData(
  gl.ARRAY_BUFFER,
  new Float32Array(WebGL.points.fullCanvas()),
  gl.STATIC_DRAW,
);
gl.enableVertexAttribArray(aTextureCoordinatesLocation);
gl.vertexAttribPointer(aTextureCoordinatesLocation, 2, gl.FLOAT, false, 0, 0);

// Make unit 0 the active texture unit.
gl.activeTexture(gl.TEXTURE0);

// Create texture.
const texture = gl.createTexture()

// Bind texture to `texture unit 0` 2D bind point.
gl.bindTexture(gl.TEXTURE_2D, texture);

// Set the parameters so we don't need mips and so we're not filtering
// and we don't repeat.
gl.texParameteri(gl.TEXTURE_2D, gl.TEXTURE_WRAP_S, gl.CLAMP_TO_EDGE);
gl.texParameteri(gl.TEXTURE_2D, gl.TEXTURE_WRAP_T, gl.CLAMP_TO_EDGE);
gl.texParameteri(gl.TEXTURE_2D, gl.TEXTURE_MIN_FILTER, gl.NEAREST);
gl.texParameteri(gl.TEXTURE_2D, gl.TEXTURE_MAG_FILTER, gl.NEAREST);

// Upload the image into the texture.
gl.texImage2D(gl.TEXTURE_2D, 0, gl.RGBA, gl.RGBA, gl.UNSIGNED_BYTE, image);

gl.useProgram(program);
gl.bindVertexArray(vao);

gl.uniform2f(uResolutionLocation, gl.canvas.width, gl.canvas.height);
gl.uniform2f(uPointerLocation, this.pointerX, this.pointerY);
gl.uniform1f(uTimeLocation, this.time);

// Tell the shader to get the texture from texture unit 0
gl.uniform1i(uImageLocation, 0);

gl.drawArrays(gl.TRIANGLES, 0, 6);
```

Success!

Manipulate the image by swapping red and blue:

```glsl
outColor = texture(u_image, v_textureCoordinates).bgra;
```

What if we want to do image processing that actually looks at other pixels?

> [!Tip]
> Since [[WebGL]] references textures in texture coordinates which go from `0.0` to `1.0` then you can calculate how much to move for 1 pixel with the simple math `onePixel = 1.0 / textureSize`.

```glsl
outColor = (
    texture(u_image, v_textureCoordinates) +
    texture(u_image, v_textureCoordinates + vec2(-onePixel.x, 0)) +
    texture(u_image, v_textureCoordinates + vec2( onePixel.x, 0))
) / 3.0;
```

Now that we know how to reference other pixels lets use a [[Convolution Kernel]] to do a bunch of common image processing.

```glsl
#version 300 es

// fragment shaders don't have a default precision so we need
// to pick one. highp is a good default. It means "high precision"
precision highp float;

// our texture
uniform sampler2D u_image;

// the convolution kernel data
uniform float u_kernel[9];
uniform float u_kernelWeight;

// the texCoords passed in from the vertex shader.
in vec2 v_texCoord;

// we need to declare an output for the fragment shader
out vec4 outColor;

void main() {
  vec2 onePixel = vec2(1) / vec2(textureSize(u_image, 0));

  vec4 colorSum =
    texture(u_image, v_texCoord + onePixel * vec2(-1, -1)) * u_kernel[0] +
    texture(u_image, v_texCoord + onePixel * vec2( 0, -1)) * u_kernel[1] +
    texture(u_image, v_texCoord + onePixel * vec2( 1, -1)) * u_kernel[2] +
    texture(u_image, v_texCoord + onePixel * vec2(-1,  0)) * u_kernel[3] +
    texture(u_image, v_texCoord + onePixel * vec2( 0,  0)) * u_kernel[4] +
    texture(u_image, v_texCoord + onePixel * vec2( 1,  0)) * u_kernel[5] +
    texture(u_image, v_texCoord + onePixel * vec2(-1,  1)) * u_kernel[6] +
    texture(u_image, v_texCoord + onePixel * vec2( 0,  1)) * u_kernel[7] +
    texture(u_image, v_texCoord + onePixel * vec2( 1,  1)) * u_kernel[8] ;
  outColor = vec4((colorSum / u_kernelWeight).rgb, 1);
}
```

```js
computeKernelWeight = (kernel) => {
  const weight = kernel.reduce((prev, curr) => prev + curr);
  return weight <= 0 ? 1 : weight;
};

// ...

const kernelLocation = gl.getUniformLocation(program, "u_kernel[0]");
const kernelWeightLocation = gl.getUniformLocation(program, "u_kernelWeight");

// ...

const edgeDetectKernel = [-1, -1, -1, -1, 8, -1, -1, -1, -1];

// Set the kernel and it's weight
gl.uniform1fv(kernelLocation, edgeDetectKernel);
gl.uniform1f(kernelWeightLocation, computeKernelWeight(edgeDetectKernel));
```

Success!
