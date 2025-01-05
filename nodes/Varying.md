---
aliases:
  - Varyings
  - In/Out Variable
context:
  - "[[Computer Graphics]]"
  - "[[GLSL]]"
---

# Varying

(aka. In/Out Variable)

Variable that passes interpolated data from a [[Vertex Shader]] to a [[Fragment Shader]].

---

Declared in the [[Vertex Shader]] and passed to the matching varying with the same name in the [[Fragment Shader]].

In the [[Vertex Shader]]:

```glsl
out vec4 v_color;

void main() {
    v_color = stuff;
}
```

In the [[Fragment Shader]]:

```glsl
in vec4 v_color;

void main() {
    stuff = v_color;
}
```
