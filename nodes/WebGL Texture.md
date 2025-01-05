---
context:
  - "[[WebGL]]"
  - "[[Texture]]"
---

# WebGL Texture

In WebGL, textures are images or [[Array|Data Arrays]].

---

**Standard Usage**: As a standard [[Texture]] holding image data, adding surface details to objects.

**Versatile Usage**: For computational tasks, as versatile [[Array|Arrays]] providing data to [[Shader|Shaders]].

**Access in Shaders**: Use the `sampler2D` or `samplerCube` [[WebGL Uniforms]] in [[GLSL]]; Access texture data with functions like `texture()`.

**Coordinates**: Texture coordinates go from `0.0` to `1.0` no matter the dimensions of the texture.

**Data Format**: See [[WebGL2 Texture Formats]].

```glsl
uniform sampler2D u_texture;

varying vec2 v_texCoord;

void main() {
    vec4 color = texture(u_texture, v_texCoord);
    gl_FragColor = color;
}
```
