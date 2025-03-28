---
context:
  - "[[Software Architecture]]"
---

# Service

Managed background process that provides specific functionality to the system or users.

---

**Persistency**: Services run persistently, often starting at boot.

**Autonomous**: Operates in the background without direct user interaction. No controlling terminal.

**Lifecycle**: Services follow a lifecycle, for example `start`, `stop`, `restart`, `reload`.

**OS Supervision**: Services are supervised and managed by different service managers, depending on the [[Operating System|OS]].
