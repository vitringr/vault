---
aliases:
  - Canvas Element
context:
  - "[[HTML]]"
---

# Canvas Element (HTML)

Versatile HTML element that provides a surface for scriptable graphics inside a [[Web Browser]] using [[JavaScript]].

---

Basic usage:

```js
const canvas = document.getElementById("canvas");
const context = canvas.getContext("2d");
```

Provides different graphic contexts:

- [[Canvas2D|2D]]
- [[WebGL]]
- [[WebGL2]]
- [[WebGPU]]
- Bitmap Renderer
