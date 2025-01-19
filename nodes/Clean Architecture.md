---
context:
  - "[[Software Design]]"
  - "[[Software Architecture]]"
---

# Clean Architecture

[[Software Design]] approach emphasizing separation of concerns and independence of components.

Organizes code into layers with clear purpose and boundaries.

---

## Layered Structure

Components are split into different layers based on their purpose in the system.

- **Core Logic (_Entities_)**: Fundamental logic or rules for the system.
- **Application Logic (_Use Cases_)**: Defines the specific tasks, actions, processes ther application performs.
- **Interface Layer (_Adapters_)**: Connects the external frameworks layer with the application logic.
- **External Layer (_Frameworks_)**: Outermost layer includes frameworks, libraries, databases, etc.

## Dependency Flow

The flow of dependencies always points inward, ensuring that the _core_ and _application logic_ remain independent of external details like _frameworks_.
