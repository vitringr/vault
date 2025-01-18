---
context:
  - "[[JavaScript]]"
  - "[[Function (Programming)]]"
---

# JavaScript Functions

Functions in JavaScript.

---

## Parameters

Input arguments to the function.

- **Default Parameters**: Functions can have _default parameters_, alowing named parameters to be initialized with default values if no value or `undefined` is passed.
- **Rest Parameters**: Functions can have an indefinite number of arguments as an array, providing a way to represent [[Variadic Function|variadic functions]].

## Arrow Function

See [[JavaScript Arrow Function]]

## Immediately-Invoked Function Expression (IIFE)

Function that is executed immediately after creation.

```javascript
// Standard IIFE:
(function() {
  // ...
})();

// Arrow Function IIFE:
(() => {
  // ...
})();

// Async IIFE:
(async () => {
  // ...
})();
```

## Arguments Object

The `arguments` object is an array-like object available in non-arrow functions.

Contains all the arguments passed to a function, allowing access to them by index, even if they are not explicitly named in the function's parameters.

## Scope

Variabes declared within a function in JavaScript are accessible only inside that function.

## Lexical Scoping

Refers to the environment enclosing that function's definition in the source code.

## Closure

A closure is a function that retains access to its outer scope, even after the outer function has finished executing.

## Function Stack

The call stack is a data structure used by JavaScript to manage function execution.

When a function is called, it is added to the stack, and when it finishes, it is removed.

## Recursion

See: [[Recursion]]

## Built-in Functions

Predefined functions provided by the language to perform common tasks.
