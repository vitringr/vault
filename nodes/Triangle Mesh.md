---
context:
  - "[[Computer Graphics]]"
---

# Triangle Mesh

Set of [[Triangle|Triangles]] connected by their common edges or vertices.

---

Essential to [[Computer Graphics]], where complex shapes and models are commonly represented by a set of connected triangles.

## Components

**Vertices**: Points in 3D space. Each triangle has exactly three vertices. Each vertex may be shared by multiple triangles. The _valence_ of a vertex refers to how many faces are connected to the vertex.

**Edges**: An edge connects two vertices. Each triangle has three edges.

**Faces**: The surfaces of the triangles themselves.

## Storage

One standard data storage format is the _indexed triangle mesh_.

Consists of two lists:

- **Vertices List**: Stores the position coordinates of vertices.
- **Triangles List**: Stores triangles by three integers for each, where the integers index into the vertices list.

Additional data per vertex is also commonly stored.
