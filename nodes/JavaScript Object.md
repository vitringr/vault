---
context:
  - "[[JavaScript]]"
  - "[[Object (Computer Science)]]"
---

# JavaScript Object

An object in JavaScript is a non-primitive [[JavaScript Data Types|data type]] storing collections of key-value pairs.

---

Keys are strings (or symbols), and values can be any data type, including other objects.

Objects are mutable and are accessed by reference.

```javascript
const person = {
  name: "Alice",
  age: 42,
  greet() {
    console.log(`Hi, I'm ${this.name}`);
  },
};

person.greet(); // "Hi, I'm Alice"
```
