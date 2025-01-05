---
tags:
  - "article"
context:
  - "[[WebGL2]]"
  - "[[WebGL Articles]]"
---

# WebGL2 Textures Article

Reference: [WebGL2 Textures Article](https://webgl2fundamentals.org/webgl/lessons/webgl-3d-textures.html)

Article about [[Texture|Textures]] in [[WebGL2]].

---

Read: [[WebGL2 Image Processing Article]]

**Setup Shaders**:
Adjust shaders in order to use [[WebGL Texture|WebGL Textures]]. Pass texture coordinates to the [[Vertex Shader]], and then straight onto the [[Fragment Shader]].

```glsl
in vec2 a_texCoord;

out vec2 v_texCoord;

void main() {
    ...

    v_texCoord = a_texCoord;
}
```

**Usage in Shaders**:
In the fragment shader we declare a uniform `sampler2D` which lets us reference a texture. We use texture coordinates passed from the vertex shader and call `texture()` to look up color from that texture.

```glsl
in vec2 v_texCoord;

uniform sampler2D u_texture;

void main() {
    outColor = texture(u_texture, v_texCoord);
}

```

**Coordinates**:
We need to setup the texture coordinates.

```glsl
// look up where the vertex data needs to go.
var positionAttributeLocation = gl.getAttribLocation(program, "a_position");
var texcoordAttributeLocation = gl.getAttribLocation(program, "a_texcoord");

...

// create the texcoord buffer, make it the current ARRAY_BUFFER
// and copy in the texcoord values
var texcoordBuffer = gl.createBuffer();
gl.bindBuffer(gl.ARRAY_BUFFER, texcoordBuffer);
setTexcoords(gl);

// Turn on the attribute
gl.enableVertexAttribArray(texcoordAttributeLocation);

// Tell the attribute how to get data out of texcoordBuffer (ARRAY_BUFFER)
var size = 2;          // 2 components per iteration
var type = gl.FLOAT;   // the data is 32bit floating point values
var normalize = true;  // convert from 0-255 to 0.0-1.0
var stride = 0;        // 0 = move forward size * sizeof(type) each iteration to get the next texcoord
var offset = 0;        // start at the beginning of the buffer
gl.vertexAttribPointer(texcoordAttributeLocation, size, type, normalize, stride, offset);
```

**Texture Image**:
We also need a texture. We can load an image since that's probably the most common way.

> [!Note] About Asynchronous Loading
> Loading images happens asynchronously. We request the image to be loaded but it takes a while for the browser to do that.
> There are generally 2 solutions to this:
>
> - Make the code wait until the image is downloaded and only then start drawing.
> - Make up some texture to use until the image is downloaded.

```glsl
// Create a texture.
var texture = gl.createTexture();
gl.bindTexture(gl.TEXTURE_2D, texture);

// Fill the texture with a 1x1 blue pixel.
gl.texImage2D(gl.TEXTURE_2D, 0, gl.RGBA, 1, 1, 0, gl.RGBA, gl.UNSIGNED_BYTE,
              new Uint8Array([0, 0, 255, 255]));

// Asynchronously load an image
var image = new Image();
image.src = "resources/f-texture.png";
image.addEventListener('load', function() {
  // Now that the image has loaded make copy it to the texture.
  gl.bindTexture(gl.TEXTURE_2D, texture);
  gl.texImage2D(gl.TEXTURE_2D, 0, gl.RGBA, gl.RGBA,gl.UNSIGNED_BYTE, image);
  gl.generateMipmap(gl.TEXTURE_2D);
}
```

Success!

**Positioning**:
Textures are referenced with _texture coordinates_ and texture coordinates go from `0.0` to `1.0` from left to right across the texture and `0.0` to `1.0` from the first pixel on the first line to the last pixel on the last line. Notice there is no "top or bottom". Top and bottom make no sense in texture space because until you draw something and orient it there is no top and bottom. What matters is you supply texture data to WebGL. The start of that data starts at texture coordinate `0, 0` and the end of that data is at `1, 1`.

To convert from pixel coordinates to texture coordinates we can use:

```
texCoordX = pixelCoordX / (width - 1);
texCoordY = pixelCoordY / (height - 1);
```

**3D Models**:
If you're making geometry in code (cubes, spheres, etc) it's usually pretty easy to compute whatever texture coordinates you want. On the other hand if you're getting 3D models from 3D modeling software, then your artists (or you) will adjust texture coordinates in those packages using a UV editor.

**Out of Range**:
If you use texture coordinates outside the `0.0` to `1.0` range, the default behavior for WebGL is to repeat the texture. `0.0` to `1.0` is one 'copy' of the texture. `1.0` to `2.0` is another copy. Even `-4.0` to `-3.0` is yet another copy.

**Disable Repeating**:
You can tell WebGL to not repeat the texture in a certain direction by using `CLAMP_TO_EDGE`:

```js
gl.texParameteri(gl.TEXTURE_2D, gl.TEXTURE_WRAP_S, gl.CLAMP_TO_EDGE);
gl.texParameteri(gl.TEXTURE_2D, gl.TEXTURE_WRAP_T, gl.CLAMP_TO_EDGE);
```

**Mirror**:
You can also tell WebGL to mirror the texture when it repeats using `gl.MIRRORED_REPEAT`.

**Mipmap**:

Read more: [[Mipmap]]

When the resolution is smaller than the original texture, when deciding what color to output pixels, using mipmap is way more performant than trying to average out pixels to determine average color.

Generally each smaller level is just a bilinear interpolation of the previous level and that's what `gl.generateMipmap` does. It looks at the biggest level and generates all the smaller levels for you.

Of course you can supply the smaller levels yourself if you want.

You can choose what WebGL does by setting the texture filtering for each texture. There are 6 modes:

- `NEAREST` = choose 1 pixel from the biggest mip
- `LINEAR` = choose 4 pixels from the biggest mip and blend them
- `NEAREST_MIPMAP_NEAREST` = choose the best mip, then pick one pixel from that mip
- `LINEAR_MIPMAP_NEAREST` = choose the best mip, then blend 4 pixels from that mip
- `NEAREST_MIPMAP_LINEAR` = choose the best 2 mips, choose 1 pixel from each, blend them
- `LINEAR_MIPMAP_LINEAR` = choose the best 2 mips. choose 4 pixels from each, blend them

Choose the most suitable mip based on design/performance requirements.

On one end you have `LINEAR_MIPMAP_LINEAR` which is arguably the best one, but also the slowest. On the other end you have `NEAREST` or `LINEAR` as they only ever use the first mip.

To set filtering you call `gl.texParameter` like this:

```js
gl.texParameteri(gl.TEXTURE_2D, gl.TEXTURE_MIN_FILTER, gl.LINEAR_MIPMAP_LINEAR);
gl.texParameteri(gl.TEXTURE_2D, gl.TEXTURE_MAG_FILTER, gl.LINEAR);
```

`TEXTURE_MIN_FILTER` is the setting used when the size of the drawing is smaller than the largest mip.

`TEXTURE_MAG_FILTER` is the setting used when the size you are drawing is larger than the largest mip. For `TEXTURE_MAG_FILTER` only `NEAREST` and `LINEAR` are valid settings.

**Texture Complete**:

> [!Warning] Texture Complete
> WebGL2 requires textures to be _"texture complete"_ otherwise they won't render.
> It means that either:
>
> 1. You've set the filtering so it only uses the first mip level, which means setting the `TEXTURE_MIN_FILTER` to either `LINEAR` or `NEAREST`.
> 2. If you are using mips then they need to be the correct sizes and you have to provide ALL OF THEM down to the `1x1` size.

The easiest way to do that is to call `gl.generateMipmap`. Otherwise if you provide your own mips you need to provide _all of them_ or you'll get an error.

**Different Textures to Different Faces**:

"How do I apply a different image to each face of a cube?"

Three answers come to mind:

1. **Complicated shaders (_BAD_)**: Make a complicated shader that references 6 textures and pass in some extra per-vertex info into the vertex shader that gets passed to the fragment shader to decide which texture to use. Ew.
2. **Planes for geometry (_Okay_)**: Draw 6 planes instead of a cube. It's not bad but it only really works for small shapes like a cube.
3. **Coordinate maps (_Best_)**: Put all of the images in 1 texture and use texture coordinates (UV mapping) to map a different part of the texture to each face of the cube. This is the best method.
