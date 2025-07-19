---
aliases:
  - WebGL2 VAO
context:
  - "[[WebGL2]]"
---

# WebGL2 Vertex Array Object

(WebGL2 VAO)

Stores configuration and management of [[Data Buffer|Data buffers]].

---

Verte Array Objects remember:

- Which buffers are used for [[WebGL Attribute|attributes]].
- How those buffers are structured.

`gl.vertexAttribPointer` describes the layout of the data.

**Analogy**: Think of the buffer as a _container_ of data, and the VAO as a _recipe_ for how to use that data.

## Setup

When configuring a VAO, `gl.vertexAttribPointer` does two critical things:

1. Links the Attribute Location to the Buffer:
   - It tells WebGL that the currently bound buffer (`gl.ARRAY_BUFFER`) will supply data for the specified attribute location.
   - This link is stored in the VAO.

2. Defines the Data Layout for the Attribute:
   - It specifies how to interpret the data in the buffer (e.g., number of components, data type, stride, and offset).

## Benefits

**Decoupling**: [[WebGL2]] is designed to decouple _resources_ (buffers) from their _configurations_ for flexibility.

**Raw Storage**: Buffers can store data without being tied to a specific configuration.

**Buffer Reuse**: You can use the same buffer with multiple configurations.
