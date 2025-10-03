---
aliases:
  - Z-Buffer
context:
  - "[[Computer Graphics]]"
---

# Depth Buffer

(aka. Z-Buffer)

Concept in [[Computer Graphics]] that deals with the depth of objects, ensuring they are rendered in a correct visual order.

---

Manages occlusion of objects - that is, which objects should be visible and which should be obscured by others.

Stores memory for the depth of every pixel on the screen.

Without a Z-buffer, distant objects might incorrectly appear in front of closer objects.
