---
aliases:
context:
---

#wip

# Monorepo

Single [[Repository]] containing multiple distinct projects, with well-defined relationships.

---

**Guide**: The [monorepo.tools](https://monorepo.tools) page is a great resource.

## Advantages

**Code Reuse**: Similar functionality can be abstracted into shared [[Library (Software Architecture)|libraries]] and directly included by projects in the monorepo.

**Atomic Updates**: Updates don't need to be separated. Each update can change the targeted code as well as its dependencies, resulting in a single atomic update.
