---
context:
  - "[[Software Architecture]]"
---

# Uncle Bob Clean Architecture

[[Software Architecture]] that organizes code into layers with a clear purpose and boundaries.

---

_My experience with this approach is that it does not solve more problems than it creates._

## Layered Structure

Components are split into different layers based on their purpose in the system.

- **Core Logic (_Entities_)**: Fundamental logic or rules for the system.
- **Application Logic (_Use Cases_)**: Defines the specific tasks, actions, processes ther application performs.
- **Interface Layer (_Adapters_)**: Connects the external frameworks layer with the application logic.
- **External Layer (_Frameworks_)**: Outermost layer includes frameworks, libraries, databases, etc.

## Dependency Flow

The flow of dependencies always points inward, ensuring that the _core_ and _application logic_ remain independent of external details like _frameworks_.
