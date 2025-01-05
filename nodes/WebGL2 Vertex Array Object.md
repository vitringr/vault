---
aliases:
  - WebGL2 VAO
context:
  - "[[WebGL2]]"
---

# WebGL2 Vertex Array Object

(WebGL2 VAO)

Container for [[WebGL Attribute]] state.

Configuration and management of [[Data Buffer|Data buffers]].

---

**Analogy**:
Think of the buffer as a _container_ of data, and the VAO as a _recipe_ for how to use that data when rendering:

1. When you create a buffer, you're filling the _container_ with ingredients (the data or storage space in the [[GPU]]).

This step prepares the data, but it _does not specify_ how it's used.

2. When you configure a VAO, you're writing a _recipe_ that specifies:

- Which _containers_ (buffers) to use.
- How to _interpret_ the data in those _containers_.

`gl.vertexAttribPointer` describes the layout of the data.

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
