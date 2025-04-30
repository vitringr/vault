---
context:
  - "[[JavaScript]]"
  - "[[Class (OOP)]]"
---

# JavaScript Class

Blueprint for creating [[JavaScript Object|JavaScript Objects]] with shared properties and behavior.

---

```javascript
class Person {
  constructor(name) {
    this.name = name;
  }

  greet() {
    console.log(`Hello, ${this.name}!`);
  }
}

const alice = new Person("Alice");
const bob = new Person("Bob");

alice.greet(); // "Hello, Alice!"
bob.greet(); // "Hello, Bob!"
```
