---
tags:
  - "article"
context:
  - "[[WebGL2]]"
  - "[[WebGL Articles]]"
---

# WebGL2 Attributes Article

Reference: [WebGL2 Attributes Article](https://webgl2fundamentals.org/webgl/lessons/webgl-attributes.html)

Article about how [[Attribute (Graphics)|attribute]] state is is setup in [[WebGL]].

---

**Definition**:
In WebGL [[WebGL Attribute|attributes]] are inputs to a [[Vertex Shader]] that get their data from [[Data Buffer|Buffers]].

WebGL will execute a user-supplied vertex shader N times when either `gl.drawArrays` or `gl.drawElements` is called. For each iteration the attributes define how to pull the data out of the buffers bound to them and supply them to the attributes inside the vertex shader.

**Intuition**:
If attributes were implemented in [[JavaScript]] they would look something like:

```js
// PSEUDO CODE

const gl = {
  arrayBuffer: null,
  vertexArray: {
    attributes: [
      { enable: ?, type: ?, normalize: ?, stride: ?, offset: ?, buffer: ?, divisor: 0 },
      { enable: ?, type: ?, normalize: ?, stride: ?, offset: ?, buffer: ?, divisor: 0 },
      { enable: ?, type: ?, normalize: ?, stride: ?, offset: ?, buffer: ?, divisor: 0 },
      { enable: ?, type: ?, normalize: ?, stride: ?, offset: ?, buffer: ?, divisor: 0 },
      { enable: ?, type: ?, normalize: ?, stride: ?, offset: ?, buffer: ?, divisor: 0 },
      { enable: ?, type: ?, normalize: ?, stride: ?, offset: ?, buffer: ?, divisor: 0 },
      { enable: ?, type: ?, normalize: ?, stride: ?, offset: ?, buffer: ?, divisor: 0 },
      { enable: ?, type: ?, normalize: ?, stride: ?, offset: ?, buffer: ?, divisor: 0 },
      { enable: ?, type: ?, normalize: ?, stride: ?, offset: ?, buffer: ?, divisor: 0 },
      { enable: ?, type: ?, normalize: ?, stride: ?, offset: ?, buffer: ?, divisor: 0 },
      { enable: ?, type: ?, normalize: ?, stride: ?, offset: ?, buffer: ?, divisor: 0 },
      { enable: ?, type: ?, normalize: ?, stride: ?, offset: ?, buffer: ?, divisor: 0 },
      { enable: ?, type: ?, normalize: ?, stride: ?, offset: ?, buffer: ?, divisor: 0 },
      { enable: ?, type: ?, normalize: ?, stride: ?, offset: ?, buffer: ?, divisor: 0 },
      { enable: ?, type: ?, normalize: ?, stride: ?, offset: ?, buffer: ?, divisor: 0 },
      { enable: ?, type: ?, normalize: ?, stride: ?, offset: ?, buffer: ?, divisor: 0 },
    ],
    elementArrayBuffer: null,
  },
};
```

As you can see above there are 16 attributes.

When you call `gl.enableVertexAttribArray(location)` or `gl.disableVertexAttribArray` you can think of it like this:

```js
// PSEUDO CODE

gl.enableVertexAttribArray = function (location) {
  const attribute = gl.vertexArray.attributes[location];
  attribute.enable = true;
};

gl.disableVertexAttribArray = function (location) {
  const attribute = gl.vertexArray.attributes[location];
  attribute.enable = false;
};
```

In other words location directly refers in the index of the attribute.

Similarly `gl.vertexAttribPointer` is used to set almost all the rest of an attribute's settings. It would look something like this:

```js
// PSEUDO CODE

// prettier-ignore
gl.vertexAttribPointer = function (location, size, type, normalize, stride, offset) {
  const attribute = gl.vertexArray.attributes[location];

  attribute.size = size;
  attribute.type = type;
  attribute.normalize = normalize;
  attribute.stride = stride ? stride : sizeof(type) * size;
  attribute.offset = offset;
  attribute.buffer = gl.arrayBuffer; // !!!
};
```

Notice when we call `gl.vertexAttribPointer` that `attribute.buffer` is set to whatever the current `gl.arrayBuffer` is set to. `gl.arrayBuffer` in the pseudo code above would be set by calling:

```js
gl.bindBuffer(gl.ARRAY_BUFFER, someBuffer);
```

```js
gl.bindBuffer = function (target, buffer) {
  switch (target) {
    case ARRAY_BUFFER:
      gl.arrayBuffer = buffer;
      break;
    case ELEMENT_ARRAY_BUFFER:
      gl.vertexArray.elementArrayBuffer = buffer;
      break;
    // ...
  }
};
```

**In the Vertex Shader**:
So next up we have vertex shaders. In vertex shaders you declare the attributes:

```glsl
#version 300 es

in vec4 a_position;
in vec2 a_texcoord;
in vec3 a_normal;

void main() {
    // ...
}
```

**Index and Location**:
When you link a vertex shader with a fragment shader by calling `gl.linkProgram(someProgram)`, WebGL (the driver/GPU/browser) decide on their own which index/location to use for each attribute.

Unless you manually assign locations (see below) you have no idea which ones they're going to pick.

You can ask WebGL which attribute it used for the variables by calling `gl.getAttribLocation`:

```js
const aPositionLocation = gl.getAttribLocation(program, "a_position");
const aTexcoordLocation = gl.getAttribLocation(program, "a_position");
const aPositionLocation = gl.getAttribLocation(program, "a_position");
```

Lets say `aPositionLocation` = `5`. That means when the vertex shader executes (when you call `gl.drawArrays` or `gl.drawElements`) the vertex shader expects you to have setup attribute 5 with the correct type, size, offset, stride, buffer, etc.

**Manual Location**:
Note that you can choose locations BEFORE linking the program by calling `gl.bindAttribLocation(program, location, nameOfAttribute)`:

```js
// Tell `gl.linkProgram` to assign `a_position` to use attribute #7
gl.bindAttribLocation(program, 7, "a_position");
```

You can also tell which location to use in your shader directly if you're using [[GLSL|GLSL ES 3.00]] shaders with:

```glsl
layout(location = 0) in vec4 a_position;
layout(location = 1) in vec2 a_texcoord;
layout(location = 2) in vec3 a_normal;
```

**Full Attribute State**:
Missing from the description above is that each attribute also has a default value. It is left out above because it is uncommon to use it.

```js
attributeValues: [
  [0, 0, 0, 1],
  [0, 0, 0, 1],
  // ...
],
vertexArray: {
  attributes: [
    { enable: ?, type: ?, normalize: ?, stride: ?, offset: ?, buffer: ?, divisor: 0 },
    { enable: ?, type: ?, normalize: ?, stride: ?, offset: ?, buffer: ?, divisor: 0 },
    // ...
  ]
}
```

You can set each attribute's value with the various `gl.vertexAttribXXX` functions. The value is used when `enable` is false. When `enable` is `true` data for the attribute is pulled from the assigned buffer.

**Vertex Array Objects (VAO)s**:

```js
const vao = gl.createVertexArray();
```

This creates the object you see attached to `gl.vertexArray` in the pseudo code above.

Calling `gl.bindVertexArray(vao)` assigns your created vertex array object as the current vertex array.

```js
// PSEUDO CODE
gl.bindVertexArray = function (vao) {
  gl.vertexArray = vao ? vao : defaultVAO;
};
```

This lets you set all of the attributes and the `ELEMENT_ARRAY_BUFFER` in the current VAO so that when you want to draw a particular shape it's one call to `gl.bindVertexArray` to effectively setup all attributes where as otherwise it would be up to one call to both `gl.bindBuffer`, `gl.vertexAttribPointer` (and possibly `gl.enableVertexAttribArray`) **per attribute**.

You can see it's arguably a good thing to use vertex array objects. Although using them often requires more organization.

**Maximum Attributes**:
WebGL2 requires that at least 16 attribute sare supported but a particular computer/browser/implementation/driver can support more.

You can find out how many are supported by calling:

```js
const maxAttributes = gl.getParameter(gl.MAX_VERTEX_ATTRIBS);
```
