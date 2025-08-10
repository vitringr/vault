---
context:
  - "[[TypeScript]]"
---

# TypeScript Assertions

[[TypeScript]] can tell the compiler to treat a value as a specific type.

---

Assertion syntax:

- Angle-bracket syntax: `<Type>value`
- As-syntax: `value as Type`

Prefer using the `as Type` syntax.

```typescript
// Angle-bracket
const length = (<string>someValue).length;

// As-syntax
const length = (someValue as string).length;
```

## Common Patterns

DOM Element Assertions:

```typescript
const input = document.getElementById("search") as HTMLInputElement;
const canvas = document.querySelector("#game-canvas") as HTMLCanvasElement;
```

Union Type Narrowing:

```typescript
function format(value: string | number) {
  return (value as string).toUpperCase() || (value as number).toFixed(2);
}
```

Object Shape Assertions:

```typescript
const user = {} as {
  name: string;
  age: number;
};
```

## Special Assertion Types

Const Assertions:

```typescript
const colors = ["red", "green", "blue"] as const;
```

Double Assertions:

```typescript
const value = unknownVar as any as CustomType; // Last resort
```

## Assertion Controls

Non-null Assertion:

```typescript
let maybeString: string | null = getString();
let definiteString: string = maybeString!; // ! operator
```

Definite Assignment Assertion:

```typescript
class Example {
  value!: string; // Tells compiler "this will be assigned later"
}
```
