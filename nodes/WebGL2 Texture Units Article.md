---
tags:
  - "article"
context:
  - "[[WebGL2]]"
  - "[[WebGL Articles]]"
---

# WebGL2 Texture Units Article

Reference: [WebGL2 Texture Units Article](https://webgl2fundamentals.org/webgl/lessons/webgl-texture-units.html)

Article about how [[Texture]] units are setup for [[WebGL Texture|WebGL Textures]] in [[WebGL2]].

---

Textures are 2D [[Array|Arrays]] of data you can pass to a [[Shader]].

In the shader you declare a _uniform sampler_ like this:

```glsl
uniform sampler2D someTexture;
```

But how does the shader know which texture to use for `someTexture`?

That's where _texture units_ come in.

**Texture Units**:
Texture units are a **global array** of references to textures.

You can imagine if WebGL was written in [[JavaScript]] it would have some global state that looks like this:

```js
const gl = {
  activeTextureUnit: 0,
  textureUnits: [
    { TEXTURE_2D: null, TEXTURE_CUBE_MAP: null, TEXTURE_3D: null, TEXTURE_2D_ARRAY: null, }, // 0
    { TEXTURE_2D: null, TEXTURE_CUBE_MAP: null, TEXTURE_3D: null, TEXTURE_2D_ARRAY: null, }, // 1
    { TEXTURE_2D: null, TEXTURE_CUBE_MAP: null, TEXTURE_3D: null, TEXTURE_2D_ARRAY: null, }, // 2
    { TEXTURE_2D: null, TEXTURE_CUBE_MAP: null, TEXTURE_3D: null, TEXTURE_2D_ARRAY: null, }, // 3
    { TEXTURE_2D: null, TEXTURE_CUBE_MAP: null, TEXTURE_3D: null, TEXTURE_2D_ARRAY: null, }, // 4
    { TEXTURE_2D: null, TEXTURE_CUBE_MAP: null, TEXTURE_3D: null, TEXTURE_2D_ARRAY: null, }, // 5
    { TEXTURE_2D: null, TEXTURE_CUBE_MAP: null, TEXTURE_3D: null, TEXTURE_2D_ARRAY: null, }, // 6
    { TEXTURE_2D: null, TEXTURE_CUBE_MAP: null, TEXTURE_3D: null, TEXTURE_2D_ARRAY: null, }, // 7
    { TEXTURE_2D: null, TEXTURE_CUBE_MAP: null, TEXTURE_3D: null, TEXTURE_2D_ARRAY: null, }, // 8
  ];
}
```

You can see above textureUnits is an array.

**Binding**:
You assign a texture to one of the _bind points_ in that array of texture units.

Lets assign `myTexture` to texture unit 5:

```js
// At init time:
const myTexture = gl.createTexture();
// Insert code to init texture here.

// ...

// At render time:
const indexOfTextureUnit = 5;
gl.activeTexture(gl.TEXTURE0 + indexOfTextureUnit);
gl.bindTexture(gl.TEXTURE_2D, myTexture);
```

You can tell the shader which texture unit you bound the texture to by calling:

```js
gl.uniform1i(someTextureUniformLocation, indexOfTextureUnit);
```

**Intuition**:
If `activeTexture` and `bindTexture` WebGL functions were implemented in JavaScript they'd look something like:

```js
// PSEUDO CODE!!!

gl.activeTexture = function (unit) {
  gl.activeTextureUnit = unit - gl.TEXTURE0; // Convert to 0 based index.
};

// ...

gl.bindTexture = function (target, texture) {
  const textureUnit = gl.textureUnits[gl.activeTextureUnit];
  textureUnit[target] = texture;
};
```

You can even imagine how other texture functions work. They all take a `target` like `gl.texImage2D(target, ...)` or `gl.texParameteri(target)`. Those would be implemented something like:

```js
// PSEUDO CODE!!!

// prettier-ignore
gl.texImage2D = function (target, level, internalFormat, width, height, border, format, type, data) {
  const textureUnit = gl.textureUnits[gl.activeTextureUnit];
  const texture = textureUnit[target];
  texture.mips[level] = convertDataToInternalFormat(internalFormat, width, height, format, type, data);
};

gl.texParameteri = function (target, pname, value) {
  const textureUnit = gl.textureUnits[gl.activeTextureUnit];
  const texture = textureUnit[target];
  texture[pname] = value;
};
```

It should be clear from the example pseudo code above that `gl.activeTexture` sets an internal global variable inside WebGL to an index of the array of texture units. From that point on, all the other texture functions take a `target`, the first argument in every texture function, that references the bind point of the current texture unit.

**Maximum Texture Units**:
WebGL requires an implementation to support at least 32 texture units. You can query how many are supported with:

```js
const maxTextureUnits = gl.getParameter(gl.MAX_COMBINED_TEXTURE_IMAGE_UNITS);
```

Note that [[Vertex Shader|Vertex Shaders]] and [[Fragment Shader|Fragment Shaders]] might have different limits on how many units each can use. You can query the limits for each with:

```js
const maxVertexShaderTextureUnits = gl.getParameter(
  gl.MAX_VERTEX_TEXTURE_IMAGE_UNITS,
);
const maxFragmentShaderTextureUnits = gl.getParameter(
  gl.MAX_TEXTURE_IMAGE_UNITS,
);
```

Each are required to support at least 16 texture units.

**Limit Example**:
Lets say:

```
maxTextureUnits = 32
maxVertexShaderTextureUnits = 16
maxFragmentShaderTextureUnits = 32
```

This means if you use for example 2 texture units in your vertex shader there are only 30 left to use in your fragment shader since the combined maximum is 32.
