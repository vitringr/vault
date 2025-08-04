---
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

## Enums

```c
enum Color { RED, GREEN, BLUE };

enum Color a = RED;
```

## Character Literals

Enclosed in single quotes (`'A'`).

Can be escape sequences:

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
