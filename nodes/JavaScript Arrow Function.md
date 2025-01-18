---
context:
- "[[JavaScript]]"
- "[[Function (Programming)]]"
---

# JavaScript Arrow Function

Shorthand syntax for defining a functions in JavaScript.

---

```javascript
const sayHello = (name) => {
    console.log("Hello, " + name);
}
```

## Syntax

Arrow functions are defined using the `=>` token:

```javascript
const f = () => {}
```

## Parameters

Parameters can be passed inside parentheses:

```javascript
const hello = (val) => "Hello" + val;
```

**Single Parameter Shorthand**: If there is only one parameter, the parentheses can be skipped:

```javascript
const hello = val => "Hello" + val;
```

## Return

**Default Return**: If the function has only one statement, and the statement returns a value, the brackets and the `return` keyword can be omitted:

```javascript
const hello = () => "Hello World!"
```

## Behavior of `this`

The handling of `this` is different in arrow functions compared to regular ones.

Arrow functions have no binding of `this`.

- **Regular Function**: the `this` keyword represents the object that called the function.
- **Arrow Function**: the `this` keyword always represents the object that defined the arrow function.

See [[Arrow Functions vs Normal Functions in JavaScript]]
