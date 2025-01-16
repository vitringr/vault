---
context:
  - "[[JavaScript]]"
  - "[[Expression (Computer Science)]]"
  - "[[Operator (Programming)]]"
---

# JavaScript Expressions and Operators

All about expressions and operators in JavaScript.

---

There are two types of expressions:

- those that have side effects
- those that purely evaluate

All complex expressions are joined by operators.

Operators are unary operators, binary operators, and one special ternary operator.

## Assignment Operators

Assigns values to its left operand based on the value of its right operand.

| Name                            | Shorthand operator | Meaning          |
| ------------------------------- | ------------------ | ---------------- |
| Assignment                      | `x = f() `         | `x = f()`        |
| Addition assignment             | `x += f() `        | `x = x + f()`    |
| Subtraction assignment          | `x -= f() `        | `x = x - f()`    |
| Multiplication assignment       | `x *= f() `        | `x = x * f()`    |
| Division assignment             | `x /= f() `        | `x = x / f()`    |
| Remainder assignment            | `x %= f() `        | `x = x % f()`    |
| Exponentiation assignment       | `x **= f() `       | `x = x ** f()`   |
| Left shift assignment           | `x <<= f() `       | `x = x << f()`   |
| Right shift assignment          | `x >>= f() `       | `x = x >> f()`   |
| Unsigned right shift assignment | `x >>>= f() `      | `x = x >>> f()`  |
| Bitwise AND assignment          | `x &= f() `        | `x = x & f()`    |
| Bitwise XOR assignment          | `x ^= f() `        | `x = x ^ f()`    |
| Bitwise OR assignment           | `x l= f()`         | `x = x l f()`    |
| Logical AND assignment          | `x &&= f() `       | `x && (x = f())` |
| Logical OR assignment           | `x ll= f() `       | `x ll (x = f())` |
| Nullish coalescing assignment   | `x ??= f() `       | `x ?? (x = f())` |

## Comparison Operators

Compares operands and returns a logical (boolean) value.

| Operator                     | Description                                                                                         | Examples returning true                |
| ---------------------------- | --------------------------------------------------------------------------------------------------- | -------------------------------------- |
| Equal (`==`)                 | Returns true if the operands are equal.                                                             | `3 == var1`, `"3" == var1`, `3 == '3'` |
| Not equal (`!=`)             | Returns true if the operands are not equal.                                                         | `var1 != 4`, `var2 != "3"`,            |
| Strict equal (`===`)         | Returns true if the operands are equal and of the same type. See also Object.is and sameness in JS. | `3 === var1`                           |
| Strict not equal (`!==`)     | Returns true if the operands are of the same type but not equal, or are of different type.          | `var1 !== "3"`, `3 !== '3'`            |
| Greater than (`>`)           | Returns true if the left operand is greater than the right operand.                                 | `var2 > var1`, `"12" > 2`              |
| Greater than or equal (`>=`) | Returns true if the left operand is greater than or equal to the right operand.                     | `var2 >= var1`, `var1 >= 3`            |
| Less than (`<`)              | Returns true if the left operand is less than the right operand.                                    | `var1 < var2`, `"2" < 12`              |
| Less than or equal (`<=`)    | Returns true if the left operand is less than or equal to the right operand.                        | `var1 <= var2`, `var2 <= 5`            |

> [!Warning] Arrow Function Syntax
> The `=>` syntax is not a comparison operator but rather the notation for arrow functions.

## Arithmetic Operators

An arithmetic operator takes numeral values (either literals or variables) as their operans and returns a single numerical value.

| Operator                       | Description                                                                                                                                                                                                                  | Example                                                                                                               |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| Remainder (`%`)                | Binary operator. Returns the integer remainder of dividing the two operands.                                                                                                                                                 | `12 % 5` returns `2`.                                                                                                 |
| Increment (`++`)               | Unary operator. Adds one to its operand. If used as a prefix operator (`++x`), returns the value of its operand after adding one; if used as a postfix operator (`x++`), returns the value of its operand before adding one. | If `x` is `3`, then `++x` sets `x` to `4` and returns `4`, whereas `x++` returns `3` and, only then, sets `x` to `4`. |
| Decrement (`--`)               | Unary operator. Subtracts one from its operand. The return value is analogous to that for the increment operator.                                                                                                            | If `x` is `3`, then `--x` sets `x` to `2` and returns `2`, whereas `x--` returns `3` and, only then, sets `x` to `2`. |
| Unary negation (`-`)           | Unary operator. Returns the negation of its operand.                                                                                                                                                                         | If `x` is `3`, then `-x` returns `-3`.                                                                                |
| Unary plus (`+`)               | Unary operator. Attempts to convert the operand to a number, if it is not already.                                                                                                                                           | `+"3"` returns `3`. `+true` returns `1`.                                                                              |
| Exponentiation operator (`**`) | Calculates the base to the exponent power, that is, base^exponent.                                                                                                                                                           | `2 ** 3` returns `8`. `10 ** -1` returns `0.1`.                                                                       |

## Bitwise Operators

Bitwise operators treats their operands as a set of 32 bits.

They perform their operations on such binary representations, but return standard JavaScript numerical values.

| Operator                     | Usage     | Description                                                                                                                                                             |
| ---------------------------- | --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Bitwise AND                  | `a & b`   | Returns a one in each bit position for which the corresponding bits of both operands are ones.                                                                          |
| Bitwise OR                   | `a l b`   | Returns a zero in each bit position for which the corresponding bits of both operands are zeros.                                                                        |
| Bitwise XOR                  | `a ^ b`   | Returns a zero in each bit position for which the corresponding bits are the same. [Returns a one in each bit position for which the corresponding bits are different.] |
| Bitwise NOT                  | `~ a`     | Inverts the bits of its operand.                                                                                                                                        |
| Left shift                   | `a << b`  | Shifts `a` in binary representation `b` bits to the left, shifting in zeros from the right.                                                                             |
| Sign-propagating right shift | `a >> b`  | Shifts `a` in binary representation `b` bits to the right, discarding bits shifted off.                                                                                 |
| Zero-fill right shift        | `a >>> b` | Shifts `a` in binary representation `b` bits to the right, discarding bits shifted off, and shifting in zeros from the left.                                            |

## Logical Operators

Typically used with Boolean values.

| Operator                           | Usage            | Description                                                                                                                                                                                             |
| ---------------------------------- | ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Logical AND (`&&`)                 | `expr1 && expr2` | Returns `expr1` if it can be converted to `false`; otherwise, returns `expr2`. Thus, when used with Boolean values, `&&` returns `true` if both operands are `true`; otherwise, returns `false`.        |
| Logical OR (`ll`)                  | `expr1 ll expr2` | Returns `expr1` if it can be converted to `true`; otherwise, returns expr2. Thus, when used with Boolean values, `ll` returns `true` if either operand is `true`; if both are `false`, returns `false`. |
| Nullish coalescing operator (`??`) | `expr1 ?? expr2` | Returns `expr1` if it is neither `null` nor `undefined`; otherwise, returns `expr2`.                                                                                                                    |
| Logical NOT (`!`)                  | `!expr`          | Returns `false` if its single operand can be converted to `true`; otherwise, returns `true`.                                                                                                            |

> [!Note] Conversions
> Examples of expressions that can be converted to `false` are those that evaluate to `null`, `0`, `0n`, `NaN`, the empty string (`""`), or `undefined`.

## BigInt Operators

Most operators that can be used with numbers can also be used with `BigInt` values as well.

## String Concatenation Operator

The concatenation operator (`+`) concatenates two string values together, returning another string that is a union of the two.

## Conditional (Ternary) Operator

The conditional operator is the only JavaScript operator that takes three operands.

The operator can have one of two values based on a condition.

Syntax: `condition ? value_if_true : value_if_false`

## Comma Operator

The comma operator (`,`) evaluates both of its operands and returns the value of the last operand.

## Unary Operators

Operations with only one operand.

- `delete`: Deletes an object's property.
- `typeof`: Returns a string indicating the type of the operand.
- `void`: Specifies an expression to be evaluated without returning a value.

## Relational Operators

Compares operands and returns a boolean.

- `in`: Returns `true` if the specified property is in the specified object.
- `instanceof`: Returns `true` if the specified object is of the specified object type.
