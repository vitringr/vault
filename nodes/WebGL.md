---
aliases:
  - Web Graphics Library
context:
  - "[[Computer Graphics]]"
  - "[[Programming Software]]"
---

# WebGL

(Web Graphics Library)

WebGL is a [[JavaScript]] [[API]] for rendering 2D and 3D graphics within a [[Web Browser]].

---

**Integration**: WebGL is based on [[OpenGL ES]] and is fully integrated with [[HTML]], allowing graphics to be rendered directly in the web browser using the [[Canvas Element (HTML)]].

```JavaScript
const canvas = document.getElementById("myCanvas");
const gl = canvas.getContext("webgl");
```

**Shaders and GLSL**: WebGL uses [[Shader|Shaders]] written in [[GLSL]] to control the graphics pipeline. Shaders are compiled and linked to create a WebGL program.

**Performance**: WebGL takes advantage of the [[GPU]] for hardware-accelerated high-performance graphics, comparable to native applications.
