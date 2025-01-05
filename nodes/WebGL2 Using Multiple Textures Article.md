---
tags:
  - "article"
context:
  - "[[WebGL2]]"
  - "[[WebGL Articles]]"
---

# WebGL2 Using Multiple Textures Article

Reference: [WebGL2 Using Multiple Textures Article](https://webgl2fundamentals.org/webgl/lessons/webgl-2-textures.html)

Article about how to use 2 or more [[Texture|Textures]] in [[WebGL2]].

---

You can reference the code from the [[WebGL2 Image Processing Article]] and update it for 2 images.

**Loading Multiple Images**:
This is a [[HTML]] and [[JavaScript]] topic.

**Shader Setup**:
Setup [[GLSL]] to use a sampler for each [[WebGL Texture]]:

```glsl
// ...

uniform sampler2D u_image0;
uniform sampler2D u_image1;

// ...

void main() {
  vec4 color0 = texture(u_image0, v_textureCoordinates);
  vec4 color1 = texture(u_image1, v_textureCoordinates);

  outColor = color0 * color1;
}
```

**Setup WebGL**:

```js
const uImage0Location = gl.getUniformLocation(program, "u_image0");
const uImage1Location = gl.getUniformLocation(program, "u_image1");

// ...

for (let i = 0; i < 2; i++) {
  gl.activeTexture(gl.TEXTURE0 + i);

  const texture = gl.createTexture();
  gl.bindTexture(gl.TEXTURE_2D, texture);

  gl.texParameteri(gl.TEXTURE_2D, gl.TEXTURE_WRAP_S, gl.CLAMP_TO_EDGE);
  gl.texParameteri(gl.TEXTURE_2D, gl.TEXTURE_WRAP_T, gl.CLAMP_TO_EDGE);
  gl.texParameteri(gl.TEXTURE_2D, gl.TEXTURE_MIN_FILTER, gl.NEAREST);
  gl.texParameteri(gl.TEXTURE_2D, gl.TEXTURE_MAG_FILTER, gl.NEAREST);

  //prettier-ignore
  gl.texImage2D(gl.TEXTURE_2D, 0, gl.RGBA, gl.RGBA, gl.UNSIGNED_BYTE, this.images[i]);
}

// ...

gl.uniform1i(uImage0Location, 0);
gl.uniform1i(uImage1Location, 1);
```

Success!

**Active Texture Unit**:
All of the texture functions work on the _active texture unit_.

The "active texture unit" is just a global variable that is the index of the texture unit you want to work with.

Each texture unit in WebGL2 has 4 targets:

- `TEXTURE_2D` target
- `TEXTURE_3D` target
- `TEXTURE_2D_ARRAY` target
- `TEXTURE_CUBE_MAP` target

Every texture function works with the specified target on the current active texture unit.

**Intuition**:
If you were to implement WebGL in [[JavaScript]] it would look something like this:

```js
const getContext = function () {
  const textureUnits = [
    {
      TEXTURE_2D: null,
      TEXTURE_3D: null,
      TEXTURE_2D_ARRAY: null,
      TEXTURE_CUBE_MAP: null,
    },
    {
      TEXTURE_2D: null,
      TEXTURE_3D: null,
      TEXTURE_2D_ARRAY: null,
      TEXTURE_CUBE_MAP: null,
    },
    {
      TEXTURE_2D: null,
      TEXTURE_3D: null,
      TEXTURE_2D_ARRAY: null,
      TEXTURE_CUBE_MAP: null,
    },
    {
      TEXTURE_2D: null,
      TEXTURE_3D: null,
      TEXTURE_2D_ARRAY: null,
      TEXTURE_CUBE_MAP: null,
    },
    {
      TEXTURE_2D: null,
      TEXTURE_3D: null,
      TEXTURE_2D_ARRAY: null,
      TEXTURE_CUBE_MAP: null,
    },
    {
      TEXTURE_2D: null,
      TEXTURE_3D: null,
      TEXTURE_2D_ARRAY: null,
      TEXTURE_CUBE_MAP: null,
    },
    {
      TEXTURE_2D: null,
      TEXTURE_3D: null,
      TEXTURE_2D_ARRAY: null,
      TEXTURE_CUBE_MAP: null,
    },
    {
      TEXTURE_2D: null,
      TEXTURE_3D: null,
      TEXTURE_2D_ARRAY: null,
      TEXTURE_CUBE_MAP: null,
    },
  ];
  const activeTextureUnit = 0;

  const activeTexture = function (unit) {
    const index = unit - gl.TEXTURE0;
    activeTextureUnit = index;
  };

  const bindTexture = function (target, texture) {
    textureUnits[activeTextureUnit][target] = texture;
  };

  const texImage2D = function (target, ...args) {
    const texture = textureUnits[activeTextureUnit][target];
    texture.image2D(...args);
  };

  const texImage3D = function (target, ...args) {
    const texture = textureUnits[activeTextureUnit][target];
    texture.image3D(...args);
  };

  return {
    activeTexture: activeTexture,
    bindTexture: bindTexture,
    texImage2D: texImage2D,
    texImage3D: texImage3D,
  };
};
```

The shaders take indices into texture units. Hopefully that makes these two lines clearer:

```js
gl.uniform1i(uImage0Location, 0); // Texture unit 0
gl.uniform1i(uImage1Location, 1); // Texture unit 1
```

When setting the uniforms you use indices for the texture units, but...

> [!Warning] Texture Unit Index
> When calling `gl.activeTexture` you have to pass in special constants `gl.TEXTURE0`, `gl.TEXTURE1`, etc.

Fortunately these constants are consecutive, so instead of:

```js
gl.activeTexture(gl.TEXTURE0); // this
gl.bindTexture(gl.TEXTURE_2D, textures[0]);

gl.activeTexture(gl.TEXTURE1); // this
gl.bindTexture(gl.TEXTURE_2D, textures[1]);
```

you could do this:

```js
gl.activeTexture(gl.TEXTURE0 + 0); // this
gl.bindTexture(gl.TEXTURE_2D, textures[0]);

gl.activeTexture(gl.TEXTURE0 + 1); // this
gl.bindTexture(gl.TEXTURE_2D, textures[1]);
```

or this:

```js
for (let i = 0; i < 2; i++) {
  gl.activeTexture(gl.TEXTURE0 + i);
  gl.bindTexture(gl.TEXTURE_2D, textures[i]);
}
```
