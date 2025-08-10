---
tags:
  - "data"
context:
  - "[[TypeScript]]"
---

# TypeScript Data Types

[[TypeScript]] extends [[JavaScript Data Types]].

---

## Core Data Types

### Primitive Types

- `boolean`: Boolean values
- `string`: Textual data
- `number`: Both integer and floating-point numbers
- `bigint`: Arbitrary-precision integers (`42n`)
- `symbol`: Unique identifiers (`Symbol('desc')`)
- `undefined`: Value when variable is not assigned
- `null`: Intentional absence of object value

### Type System Specials

- `any`: Opts out of type checking (avoid when possible)
- `object`: Any non-primitive value (differs from `Object` and `{}`)
- `unknown`: Type-safe alternative to any (requires type checking before use)
- `never`: Represents unreachable code (e.g., functions that always throw errors)
- `void`: Return type of functions that don't return a value

## Structural Types

### Object Types

- **Interface**: Defines object shape contracts
- **Class**: Blueprint for creating objects with properties and methods
- **Object**: Non-primitive type (key-value pairs)

### Collection Types

- **Array**: Ordered lists (`number[]` or `Array<number>` syntax)
- **ReadonlyArray**: Read-only ordered lists (`ReadonlyArray<number>`)
- **Tuple**: Fixed-length array with specified types (`[string, number]`)

### Special Constructs

- **Enum**: Named constant values (`enum Color { Red, Green }`)
- **Literal Types**: Exact values (`let x: "hello" = "hello"`)

## Utility Types

Common:

- `Partial<T>`: Makes all properties optional.
- `Required<T>`: Makes all properties required.
- `Readonly<T>`: Makes properties immutable.
- `Record<K, T>`: Defines an object with keys `K` and values `T`.
- `Pick<T, K>`: Selects specific properties from `T`.
- `Omit<T, K>`: Removes specific properties from `T``.

Less Common:

- `Exclude<T, U>`: Excludes types from `T` that match `U`.
- `Extract<T, U>`: Keeps types from `T` that match `U`.
- `NonNullable<T>`: Removes null and undefined from `T`.
- `ReturnType<T>`: Gets the return type of a function.
- `Parameters<T>`: Gets the parameters of a function as a tuple.
- `Awaited<T>`: Unwraps Promise types to their resolved value.

## Advanced Types

- **Union Types**: Multiple possible types (`string | number`)
- **Intersection Types**: Combines multiple types (`TypeA & TypeB`)
- **Type Aliases**: Custom type definitions (`type Point = { x: number }`)
- **Generics**: Reusable type variables (`Array<T>`)
- **Conditional Types**: `T extends U ? X : Y`
- **Template Literal Types**: ``` type EventName = `click-${string}` ```
- **Recursive Types**: `type Json = string | number | Json[] | { [key: string]: Json }`
