---
context:
  - "[[Programming Paradigm]]"
  - "[[Imperative Programming]]"
---

# Procedural Programming

Programming paradigm that structures programs as series of [[Function (Programming)|Procedures]] calling each other.

---

**Modularity**: Procedural programming implements [[Modular Design]] by organizing logic into reusable procedures, and organizing procedures into separate modules, each of which having a specific purpose.

## Modules

Modules can be divided into two major groups:

- **Logic**: Pure functions. Should not contain internal state, and should not reach out for external state.
- **State**: May contain internal state and may reach out for external state.

The relationship between logic and state modules is strictly one way - state modules can call logic modules, but not the other way around.
