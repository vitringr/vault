---
context:
  - "[[WebGL]]"
  - "[[WebGL2]]"
---

# WebGL Automatic Normalization When Sampling

WebGL automatically normalizes values when sampling [[Texture|Textures]] using the `texture()` function in the [[Shader]].

---

For example, it will automatically normalize `UNSIGNED_BYTE` values from `[0, 255]` range to `[0, 1]` range.

```js
// Texture with 100x100 pixels
const level = 0;
const internalFormat = gl.RGB8;
const width = 100;
const height = 100;
const border = 0;
const format = gl.RGB;
const type = gl.UNSIGNED_BYTE;

const bytesPerPixel = 3;
const totalBytes = width * height * bytesPerPixel;

const colors: number[] = [];
for (let i = 0; i < totalBytes; i++) {
  colors.push(Math.random() * 256); // Passing 0 to 256 numbers - Bytes.
}

const data = new Uint8Array(colors);
gl.texImage2D(gl.TEXTURE_2D, level, internalFormat, width, height, border, format, type, data);
```

In the [[Fragment Shader]], this will just work:

```glsl
void main() {
  vec4 texturePixel = texture(u_image, v_textureCoordinates); // Normalization!

  outColor = texturePixel; // Works as expected in the 0 to 1 float range.
}
```
