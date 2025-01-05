---
context:
  - "[[Software Design]]"
  - "[[SOLID Principles]]"
---

# Dependency Inversion Principle

High-level modules should not depend on low-level modules.

Both should depend on abstractions.

Abstractions should not depend on details.

Details should depend on abstractions.

---

Depend on abstractions (interfaces) rather than concrete implementations.

High-level modules should not import anything from low-level modules.

## Example

Instead of:

`class A ==> class B ==> class C`

do:

`class A ==> interface A <== class B ==> interface C <== class C`
