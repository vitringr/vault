---
context:
  - "[[JavaScript]]"
  - "[[Function (Programming)]]"
---

# Arrow Functions vs Normal Functions in JavaScript

Key differences between [[Arrow Function (JavaScript)]] and normal functions in [[JavaScript]].

---

**Behavior of `this`**:
Normal `function` declarations use dynamic `this`, depending on how the function is called.

Arrow functions always bind `this` to the surrounding context.

```js
const someObject = {
  value: 42,

  normalMethod: function () {
    console.log(this.value);
  },

  arrowMethod: () => {
    console.log(this.value); // Error
  },
};

someObject.normalMethod(); // 42
someObject.arrowMethod(); // undefined
```

**Hoisting**:
Normal `function` declarations are hoisted, so they can be called before they are defined in the code.

Arrow functions are not hoisted and behave like variables, throwing an error if accessed before declaration.

```js
console.log(normal()); // Works
function normal() {
  return "hoisted";
}

console.log(arrow()); // Error
const arrow = () => "not hoisted";
```

**Constructors**:
Arrow functions cannot be used as [[Class (OOP)]] [[Constructor (OOP)|constructors]].
