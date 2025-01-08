---
context:
  - "[[JavaScript]]"
  - "[[Variable (Programming)]]"
---

# JavaScript Variable

All about JavaScript variables.

---

## Declaration
Variables are declared by a keyword followed by the variable's name.

Keywords:
- **var**: declares a function-scoped or globally-scoped variable, optionally initializing it to a value.
- **let**: declares a block-scoped local variable, optionally initializing it to a value.
- **const**: declares a block-scoped (much like the `let` keyword) variable that cannot be changed through reassignment and it cannot be re-declared.

> [!Tip] Best Practices
> You should generally use `const`. Only use `let` when you can't use `const`. Avoid using `var`.

Variables can also be declared automatically without a keyword.

> [!Warning] Bad Practice
> Automatic declaration is a bad practice. Always explicitly declare variables.

## Naming Rules

Variable names can only consist of:
- **letters**: _a_ to _z_ and _A_ to _Z_
- **numbers**: *0* to *9*
- **underscores**: *_*
- **dollar sign**: *$*

Variable names cannot start with a number.

Variable names must start with a letter, dollar sign, or an underscore.

Variable names cannot be certain reserved keywords, such as `Javascript`, `true`, `this`, etc.

Variable names cannot contain spaces.

## Hoisting

See [[JavaScript Hoisting]]

## Scope

See [[Scope (Computer Science)]]

The scope of a JavaScript variable depends on the keyword used to declare it.

There are three types of JavaScript scope:
- **Global Scope**: Variables declared globally (outside any function or block) have global scope. They can be accessed from anywhere in the JavaScript program. `var`, `let`, `const` can all provide global scope. Automatic declarations are also global scope.
- **Function Scope**: Variables declared inside a function are only accessible within that function. `var`, `let`, `const` all provide function scope.
- **Block Scope**: Variables declared inside a block are only accessible within that block. Only `let` and `const` provide block scope. Variables declared with `var` do not have block scope.
