---
tags:
  - "data"
context:
  - "[[C (Programming Language)]]"
  - "[[Operator (Programming)]]"
---

# C Operators

Operators in the C programming language.

---

## Arithmetic Operators

| Operator | Description         | Example | Result (`a=10`, `b=3`) |
| -------- | ------------------- | ------- | ---------------------- |
| `+`      | Addition            | `a + b` | `13`                   |
| `-`      | Subtraction         | `a - b` | `7`                    |
| `*`      | Multiplication      | `a * b` | `30`                   |
| `/`      | Division            | `a / b` | `3` (integer division) |
| `%`      | Modulus (Remainder) | `a % b` | `1`                    |
| `++`     | Increment           | `a++`   | `a` becomes `11`       |
| `--`     | Decrement           | `a--`   | `a` becomes `9`        |

## Relational Operators

| Operator | Description      | Example  | Result (if `a=5`, `b=10`) |
| -------- | ---------------- | -------- | ------------------------- |
| `==`     | Equal to         | `a == b` | `0`                       |
| `!=`     | Not equal to     | `a != b` | `1`                       |
| `>`      | Greater than     | `a > b`  | `0`                       |
| `<`      | Less than        | `a < b`  | `1`                       |
| `>=`     | Greater or equal | `a >= b` | `0`                       |
| `<=`     | Less or equal    | `a <= b` | `1`                       |

## Logical Operators

| Operator | Description | Example    | Result (if `a=1`, `b=0`) |
| -------- | ----------- | ---------- | ------------------------ |
| `&&`     | Logical AND | `a && b`   | `0`                      |
| `\|\|`   | Logical OR  | `a \|\| b` | `1`                      |
| `!`      | Logical NOT | `!a`       | `0`                      |

## Bitwise Operators

| Operator | Description | Example  | Result (if `a=5` (`0101`), `b=3` (`0011`)) |
| -------- | ----------- | -------- | ------------------------------------------ |
| `&`      | Bitwise AND | `a & b`  | `1` (`0001`)                               |
| `\|`     | Bitwise OR  | `a \| b` | `7` (`0111`)                               |
| `^`      | Bitwise XOR | `a ^ b`  | `6` (`0110`)                               |
| `~`      | Bitwise NOT | `~a`     | `-6` (2's complement)                      |
| `<<`     | Left shift  | `a << 1` | `10` (`1010`)                              |
| `>>`     | Right shift | `a >> 1` | `2` (`0010`)                               |

## Assignment Operators

| Operator | Example   | Equivalent to |
| -------- | --------- | ------------- |
| `=`      | `a = 5`   | `a = 5`       |
| `+=`     | `a += 3`  | `a = a + 3`   |
| `-=`     | `a -= 2`  | `a = a - 2`   |
| `*=`     | `a *= 4`  | `a = a * 4`   |
| `/=`     | `a /= 2`  | `a = a / 2`   |
| `%=`     | `a %= 3`  | `a = a % 3`   |
| `&=`     | `a &= b`  | `a = a & b`   |
| `\|=`    | `a \|= b` | `a = a \| b`  |
| `^=`     | `a ^= b`  | `a = a ^ b`   |
| `<<=`    | `a <<= 1` | `a = a << 1`  |
| `>>=`    | `a >>= 1` | `a = a >> 1`  |

## Miscellaneous Operators

| Operator | Description      | Example          | Usage                           |
| -------- | ---------------- | ---------------- | ------------------------------- |
| `?:`     | Ternary Operator | `a > b ? a : b`  | Returns `a` if true, else `b`   |
| `,`      | Comma Operator   | `a = (b=2, b+3)` | Evaluates multiple expressions  |
| `sizeof` | Size in Bytes    | `sizeof(int)`    | Returns `4` (on 32-bit systems) |
| `&`      | Address-of       | `&a`             | Returns memory address of `a`   |
| `*`      | Dereference      | `*ptr`           | Accesses value at pointer `ptr` |

## Operator Precedence

| Category       | Operators                                                   | Associativity |
| -------------- | ----------------------------------------------------------- | ------------- |
| Parentheses    | `()`                                                        | Left-to-Right |
| Unary          | `++`, `--`, `!`, `~`, `+`, `-`, `*`, `&`, `(type)` `sizeof` | Right-to-Left |
| Multiplicative | `*`, `/`, `%`                                               | Left-to-Right |
| Additive       | `+`, `-`                                                    | Left-to-Right |
| Shift          | `<<`, `>>`                                                  | Left-to-Right |
| Relational     | `<`, `<=`, `>`, `>=`                                        | Left-to-Right |
| Equality       | `==`, `!=`                                                  | Left-to-Right |
| Bitwise AND    | `&`                                                         | Left-to-Right |
| Bitwise XOR    | `^`                                                         | Left-to-Right |
| Bitwise OR     | `\|`                                                        | Left-to-Right |
| Logical AND    | `&&`                                                        | Left-to-Right |
| Logical OR     | `\|\|`                                                      | Left-to-Right |
| Ternary        | `?:`                                                        | Right-to-Left |
| Assignment     | `=`, `+=`, `-=`, etc.                                       | Right-to-Left |
| Comma          | `,`                                                         | Left-to-Right |
