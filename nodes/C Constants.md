---
tags:
  - "data"
aliases:
  - C Literals
context:
  - "[[C (Programming Language)]]"
  - "[[Constant (Programming)]]"
---

#wip

# C Constants

Constants in the C programming language.

---

See [[C Data Types]]

## Named Constants

Use `const` or `#define` to create named constants.

```c
#define A 42
const int B = 42;
```

| Feature     | `const` Keyword            | `#define` Macro          |
| ----------- | -------------------------- | ------------------------ |
| Type Safety | Yes (has a data type)      | No (text replacement)    |
| Memory      | Allocated in memory        | No memory (preprocessor) |
| Scope       | Follows C scoping rules    | Global (no scope)        |
| Debugging   | Easier (symbolic in debug) | Harder (replaced text)   |

### Enums

Use `enum` to create user-defined named integer constants.

Default values start at `0` and increment by `1`.

```c
enum Color { RED, GREEN, BLUE };

enum Color a = RED;
```

## Character Literals

Enclosed in single quotes (`'A'`).

```c
char letter = 'A';     // Simple character
char newline = '\n';   // Escape sequence
char null_char = '\0'; // Null terminator
```

### Escape sequences:

| Escape sequence | Character represented                                                                |
| --------------- | ------------------------------------------------------------------------------------ |
| `\a`            | Alert (Beep, Bell)                                                                   |
| `\b`            | Backspace                                                                            |
| `\e`            | Escape character                                                                     |
| `\f`            | Formfeed Page Break                                                                  |
| `\n`            | Newline (Line Feed); see below                                                       |
| `\r`            | Carriage Return                                                                      |
| `\t`            | Horizontal Tab                                                                       |
| `\v`            | Vertical Tab                                                                         |
| `\\             | Backslash                                                                            |
| `\'`            | Apostrophe or single quotation mark                                                  |
| `\"`            | Double quotation mark                                                                |
| `\?`            | Question mark (used to avoid trigraphs)                                              |
| `\nnn`          | The byte whose numerical value is given by `nnn` interpreted as an octal number      |
| `\xhh`...       | The byte whose numerical value is given by `hh`… interpreted as a hexadecimal number |
| `\uhhhh`        | Unicode code point below `10000` hexadecimal                                         |
| `\Uhhhhhhhh`    | Unicode code point where `h` is a hexadecimal digit                                  |

## String Literals

Enclosed in double quotes (`"Hello"`).

Stored as null-terminated `char` arrays (`'H','e','l','l','o','\0'`).

**Immutable**: Modifying them leads to undefined behavior.

```c
char str[] = "Hello";      // Modifiable copy
const char *ptr = "World"; // Read-only (best practice)
printf("%s", "C Programming"); // Direct usage
```

**Quotes**: Note that `'A'` is a single character (1 byte) `A`, while `"A"` is a string (2 bytes) `A` + `\0`.
