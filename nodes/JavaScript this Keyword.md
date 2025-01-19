---
context:
  - "[[JavaScript]]"
---

# JavaScript this Keyword

The `this` keyword in JavaScript refers to an object, depending on how or where it is being invoked.

---

- **Global Scope**: `this` refers to the global object (`window` or `global`).
- **Object Method**: `this` refers to the object the method is called on.
- **Arrow Function**: `this` is lexically bound and refers to the surrounding scope.
- **Constructor Function**: `this` refers to the instance being created.
- **Event Handlers**: `this` refers to the element the event is bound to.

## Explicit Binding

The `this` value can be manually set using methods like `call`, `apply`, or `bind`.

This allows for explicit control over what object `this` refers to during function execution, overriding the default behavior.
