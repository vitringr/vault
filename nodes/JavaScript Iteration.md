---
context:
  - "[[JavaScript]]"
  - "[[Iteration]]"
---

# JavaScript Iteration

All about iteration and loops in JavaScript.

---

## Loops

**`while` Loop**: Executes as long as the test condition evaluates to `true`.

```javascript
let count = 0;
while (count < 3) {
  console.log(count); // Outputs: 0, 1, 2
  count++;
}
```

**`do...while` Loop**: Executes the block at least once before continuing with the `while` loop.

```javascript
let count = 0;
do {
  console.log(count); // Outputs: 0
  count++;
} while (count < 1);
```

**`for` Loop**: Combines initialization, condition, and increment/decrement into a single statement.

```javascript
for (let i = 0; i < 5; i++) {
  console.log(i); // Outputs: 0, 1, 2, 3, 4
}
```

**`for...in` Loop**: Iterates over enumerable properties (keys) of objects or arrays.

```javascript
const obj = { a: 1, b: 2 };
for (let key in obj) {
  console.log(key, obj[key]); // Outputs: a 1, b 2
}
```

**`for...of` Loop**: Iterates over iterable objects.

```javascript
const arr = [1, 2, 3];
for (let value of arr) {
  console.log(value); // Outputs: 1, 2, 3
}
```

## Loop Statements

**Continue**: The `continue` statement is used to skip the current iteration and go to the next.

**Break**: The `break` statement is used to break out of a loop.

## Array Iteration Methods

JavaScript arrays offer iterations methods in the [[Functional ]]

forEach
map
filter
reduce
