---
context:
  - "[[Programming Paradigm]]"
  - "[[Software Design]]"
---

# Reactive Programming

Programming paradigm focused on reacting to changes in data or state automatically.

---

Example:

```js
var b = 1;
var c = 2;
var a = b + c;

b = 10;

print(a);
```

In a reactive programming setting, the printed value of a should be `12` instead of `3`, as it automatically reacts to the change `b = 10`.
